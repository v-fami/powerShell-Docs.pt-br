---
ms.date: 06/12/2017
keywords: jea,powershell,segurança
title: Configurações de Sessão de JEA
ms.openlocfilehash: 1b598522d43b2c1a26a739a67cee5181b21a7c32
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655456"
---
# <a name="jea-session-configurations"></a>Configurações de Sessão de JEA

> Aplica-se a: Windows PowerShell 5.0

Um ponto de extremidade JEA é registrado em um sistema através da criação e registro de um arquivo de configuração de sessão do PowerShell de uma maneira específica.
As configurações de sessão determinam *quem* pode usar o ponto de extremidade JEA e a quais funções eles terão acesso.
Elas também definem configurações globais que se aplicam aos usuários de qualquer função na sessão JEA.

Este tópico descreve como criar um arquivo de configuração de sessão do PowerShell e registrar um ponto de extremidade JEA.

## <a name="create-a-session-configuration-file"></a>Criar um arquivo de configuração de sessão

Para registrar um ponto de extremidade JEA, você precisa especificar como esse ponto de extremidade deve ser configurado.
Há muitas opções a serem considerados aqui e as mais importantes delas são: quem devem ter acesso ao ponto de extremidade JEA, quais funções serão atribuídas a eles, qual identidade será usada pelo JEA nos bastidores e qual será o nome do ponto de extremidade JEA.
Todas essas opções são definidas em um arquivo de configuração de sessão do PowerShell, que é um arquivo de dados do PowerShell que termina com uma extensão .pssc.

Para criar um arquivo de configuração esqueleto de sessão para pontos de extremidade JEA, execute o comando a seguir.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\MyJEAEndpoint.pssc
```

> [!TIP]
> Apenas as opções de configuração mais comuns são incluídas no arquivo esqueleto por padrão.
> Use a opção `-Full` para incluir todas as configurações aplicáveis no PSSC gerado.

Você pode abrir o arquivo de configuração de sessão em qualquer editor de texto.
O campo `-SessionType RestrictedRemoteServer` indica que a configuração da sessão será usada pelo JEA para gerenciamento seguro.
As sessões configuradas dessa forma funcionarão no [modo NoLanguage](https://technet.microsoft.com/library/dn433292.aspx) e só terão estes oito comandos (e aliases) padrão disponíveis:

- Clear-Host (cls, limpar)
- Exit-PSSession (exsn, sair)
- Get-Command (gcm)
- Get-FormatData
- Get-Help
- Measure-Object (medida)
- Out-Default
- Select-Object (selecionar)

Não estão disponíveis provedores de PowerShell, nem programas externos (executáveis, scripts, etc).

Há vários outros campos que você pode configurar para a sessão JEA.
Eles são abordados nas seções a seguir.

### <a name="choose-the-jea-identity"></a>Escolha a identidade JEA

Nos bastidores, o JEA precisa de uma identidade (conta) para usar ao executar os comandos do usuário conectado.
Você pode decidir qual identidade JEA será usada no arquivo de configuração de sessão.

#### <a name="local-virtual-account"></a>Conta Virtual Local

Se as funções com suporte nesse ponto de extremidade JEA são usadas para gerenciar o computador local e uma conta de administrador local for suficiente para executar os comandos com êxito, você deverá configurar o JEA para usar uma conta virtual local.
As contas virtuais são contas temporárias exclusivas para um usuário específico e permanecem ativas apenas durante a sessão do PowerShell.
Em um servidor membro ou estação de trabalho, as contas virtuais pertencem ao grupo de **Administradores** do computador local e têm acesso à maioria dos recursos do sistema.
Em um Controlador de Domínio do Active Directory, as contas virtuais pertencem ao grupo **Administradores do domínio** do domínio.

```powershell
# Setting the session to use a virtual account
RunAsVirtualAccount = $true
```

Se as funções com suporte pela configuração de sessão não exigem esses privilégios amplos, você pode, opcionalmente, especificar os grupos de segurança aos quais a conta virtual pertencerá.
Em um servidor membro ou estação de trabalho, os grupos de segurança especificados devem ser grupos locais e não grupos de um domínio.

Quando um ou mais grupos de segurança forem especificados, a conta virtual não pertencerá mais ao grupo local de administradores local ou grupo de administradores de domínio.

```powershell
# Setting the session to use a virtual account that only belongs to the NetworkOperator and NetworkAuditor local groups
RunAsVirtualAccount = $true
RunAsVirtualAccountGroups = 'NetworkOperator', 'NetworkAuditor'
```
> [!NOTE]
> As contas virtuais recebem temporariamente o Logon como um serviço certo na política de segurança de servidor local.  Se um do VirtualAccountGroups especificado já tem esse direito na política, a conta virtual individual não será adicionada e removida da política.  Isso pode ser útil em cenários como controladores de domínio onde as revisões de diretiva de segurança de controlador de domínio intimamente são auditadas.  Isso só está disponível no Windows Server 2016 com novembro de 2018 ou distribuição mais recente e 2019 do Windows Server com o de janeiro de 2019 ou pacote cumulativo de atualizações posteriores.

#### <a name="group-managed-service-account"></a>Conta de Serviço Gerenciado de Grupo


Para cenários que exigem que o usuário JEA acesse recursos de rede, como outros computadores ou serviços Web, uma gMSA (conta de serviço gerenciado de grupo) é uma identidade mais apropriada a ser usada.
As contas gMSA fornecem uma identidade de domínio que pode ser usada para autenticar para recursos em qualquer computador no domínio.
Os direitos concedidos pela conta gMSA são determinados pelos recursos que você está acessando.
Você não terá automaticamente direitos de administrador em todos os computadores ou serviços, a menos que o administrador de computador/serviços tenha explicitamente concedido privilégios de administrador à conta gMSA.

```powershell
# Configure JEA sessions to use the gMSA account in the local computer's domain with the sAMAccountName of 'MyJEAgMSA'
GroupManagedServiceAccount = 'Domain\MyJEAgMSA'
```

As contas gMSA só devem ser usadas quando for necessário o acesso aos recursos de rede por alguns motivos:

- É mais difícil rastrear ações de um usuário ao usar uma conta gMSA, pois cada usuário compartilha a mesma identidade Run As. Você precisará consultar transcrições e logs de sessão do PowerShell para correlacionar os usuários e suas ações.

- A conta gMSA pode ter acesso a vários recursos de rede que o usuário conectado não necessita acessar. Sempre tente limitar as permissões efetivas em uma sessão JEA para seguir o princípio de privilégio mínimo.

> [!NOTE]
> As contas de serviço gerenciado de grupo estão disponíveis apenas no Windows PowerShell 5.1 ou mais recente e em computadores que ingressaram no domínio.


#### <a name="more-information-about-run-as-users"></a>Mais informações sobre usuários Run As

Informações adicionais sobre identidades Run As e como elas influenciam na segurança de uma sessão JEA podem ser encontradas no artigo [considerações de segurança](security-considerations.md).

### <a name="session-transcripts"></a>Transcrições de sessão

É recomendável configurar um arquivo de configuração de sessão JEA para registrar automaticamente as transcrições de sessões de usuários.
As transcrições de sessão do PowerShell contêm informações sobre o usuário conectado, a identidade Run As atribuída a ele e os comandos executados pelo usuário.
Elas podem ser úteis para uma equipe de auditoria que precisa entender quem executou uma alteração específica em um sistema.

Para configurar a transcrição automática no arquivo de configuração de sessão, forneça um caminho para uma pasta em que as transcrições devem ser armazenadas.

```powershell
TranscriptDirectory = 'C:\ProgramData\JEAConfiguration\Transcripts'
```

A pasta especificada deve ser configurada para impedir que os usuários modifiquem ou excluam qualquer dado nela.
As transcrições são gravadas na pasta pela conta Sistema Local, que requer acesso de leitura e gravação no diretório.
Os usuários padrão não devem ter nenhum acesso à pasta e um conjunto limitado de administradores de segurança deve ter acesso para auditar as transcrições.

### <a name="user-drive"></a>Unidade de usuário

Se os usuários que estão se conectando precisarem copiar arquivos do ou para o ponto de extremidade JEA para executar um comando, você poderá habilitar a unidade do usuário no arquivo de configuração de sessão.
A unidade de usuário é um [PSDrive](https://msdn.microsoft.com/powershell/scripting/getting-started/cookbooks/managing-windows-powershell-drives) que é mapeada para uma pasta exclusiva para cada usuário que está se conectando.
Essa pasta serve como um espaço para que eles possam copiar arquivos do sistema ou para o sistema, sem fornecer acesso ao sistema de arquivos completo ou expor o provedor FileSystem.
Os conteúdos da unidade de usuário são persistentes entre as sessões para se adaptar a situações em que a conectividade de rede pode ser interrompida.

```powershell
MountUserDrive = $true
```

Por padrão, a unidade de usuário permite que seja armazenado um máximo de 50 MB de dados por usuário.
Você pode limitar a quantidade de dados que um usuário pode consumir com o campo *UserDriveMaximumSize*.

```powershell
# Enables the user drive with a per-user limit of 500MB (524288000 bytes)
MountUserDrive = $true
UserDriveMaximumSize = 524288000
```

Se quiser que os dados na unidade de usuário não sejam persistentes, você poderá configurar uma tarefa agendada no sistema para limpar automaticamente a pasta toda noite.

> [!NOTE]
> A unidade de usuário só está disponível no Windows PowerShell 5.1 ou mais recente.

### <a name="role-definitions"></a>Definições de função

As definições de função em um arquivo de configuração de sessão definem o mapeamento de *usuários* para as *funções*.
Cada usuário ou grupo incluído nesse campo automaticamente receberá permissão para o ponto de extremidade JEA quando ele for registrado.
Cada usuário ou grupo pode ser incluído como uma chave na tabela de hash somente uma vez, mas pode ser atribuído a várias funções.
O nome da capacidade de função deve ser o nome do arquivo de capacidade de função, sem a extensão .psrc.

```powershell
RoleDefinitions = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}
```

Se um usuário pertencer a mais de um grupo na definição de função, ele receberá acesso às funções de cada grupo.
Se duas funções de concedem acesso aos mesmos cmdlets, o conjunto de parâmetros mais permissivo será concedido ao usuário.

Ao especificar usuários ou grupos locais no campo de definições de função, use o nome do computador (não *localhost* ou *.*) antes da barra invertida.
Você pode verificar o nome do computador inspecionando a variável `$env:computername`.

```powershell
RoleDefinitions = @{
    'MyComputerName\MyLocalGroup' = @{ RoleCapabilities = 'DnsAuditor' }
}
```

### <a name="role-capability-search-order"></a>Ordem de pesquisa de capacidade de função
Conforme mostrado no exemplo acima, os recursos de função são referenciados pelo nome simples (nome sem a extensão) do arquivo de capacidade de função.
Se vários recursos de função estão disponíveis no sistema com o mesmo nome simples, o PowerShell usará sua ordem de pesquisa implícita para selecionar o arquivo de capacidade de função efetivo.
Ele **não** dará acesso a todos os arquivos de capacidade de função com o mesmo nome.

A JEA usa a variável de ambiente do `$env:PSModulePath` para determinar quais caminhos verificar para os arquivos de capacidade da função.
Em cada um desses caminhos, a JEA procurará módulos válidos do PowerShell que contenham uma subpasta "RoleCapabilities".
Como com a importação de módulos, a JEA prefere as capacidades de função que são fornecidas com o Windows para capacidades de função personalizadas com o mesmo nome.
Para todos os outros conflitos de nomenclatura, a precedência é determinada pela ordem na qual o Windows enumera os arquivos no diretório (não é garantido que seja em ordem alfabética).
O primeiro arquivo de capacidade de função encontrado que corresponder ao nome será usado para o usuário que está se conectando.

Como a ordem de pesquisa de capacidade de função não é determinista quando duas ou mais capacidades de função compartilham o mesmo nome, é **altamente recomendável** garantir que as capacidades de função tenham nomes exclusivos em seu computador.

### <a name="conditional-access-rules"></a>Regras de acesso condicional

Todos os usuários e grupos incluídos no campo RoleDefinitions recebem automaticamente acesso a pontos de extremidade JEA.
As regras de acesso condicional permitem que você refine esse acesso e exigem que os usuários façam parte de grupos de segurança adicionais, o que não afeta as funções atribuídas a eles.
Isso pode ser útil se você deseja integrar uma solução de gerenciamento de acesso privilegiado "just-in-time", uma autenticação de cartão inteligente ou outra solução de autenticação multifator com o JEA.

As regras de acesso condicional são definidas no campo RequiredGroups em um arquivo de configuração de sessão.
Lá, você pode fornecer uma tabela de hash (opcionalmente aninhada) que usa chaves 'E' e 'Ou' para construir suas regras.
Aqui estão alguns exemplos de como utilizar esse campo:

```powershell
# Example 1: Connecting users must belong to a security group called "elevated-jea"
RequiredGroups = @{ And = 'elevated-jea' }

# Example 2: Connecting users must have signed on with 2 factor authentication or a smart card
# The 2 factor authentication group name is "2FA-logon" and the smart card group name is "smartcard-logon"
RequiredGroups = @{ Or = '2FA-logon', 'smartcard-logon' }

# Example 3: Connecting users must elevate into "elevated-jea" with their JIT system and have logged on with 2FA or a smart card
RequiredGroups = @{ And = 'elevated-jea', @{ Or = '2FA-logon', 'smartcard-logon' }}
```

> [!NOTE]
> As regras de acesso condicional só estão disponíveis no Windows PowerShell 5.1 ou mais recente.

### <a name="other-properties"></a>Outras propriedades
Os arquivos de configuração de sessão também podem fazer tudo o que um arquivo de recurso de função pode fazer, mas sem a capacidade de fornecer aos usuários que estão se conectando o acesso a comandos diferentes.
Se quiser permitir que todos os usuários acessem provedores, funções ou cmdlets específicos, você poderá fazer isso diretamente no arquivo de configuração de sessão.
Para obter uma lista completa das propriedades com suporte no arquivo de configuração de sessão, execute `Get-Help New-PSSessionConfigurationFile -Full`.

## <a name="testing-a-session-configuration-file"></a>Testando um arquivo de configuração de sessão

Você pode testar uma configuração de sessão usando o cmdlet [Test-PSSessionConfigurationFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/test-pssessionconfigurationfile).
É altamente recomendável que você teste o arquivo de configuração de sessão caso tenha editado o arquivo pssc manualmente usando um editor de texto, a fim de garantir que a sintaxe está correta.
Se um arquivo de configuração de sessão não passar nesse teste, não poderá ser registrado com êxito no sistema.

## <a name="sample-session-configuration-file"></a>Arquivo de configuração de sessão de exemplo

Abaixo há um exemplo completo que mostra como criar e validar uma configuração de sessão para o JEA.
Observe que as definições de função são criadas e armazenadas na variável `$roles` para conveniência e legibilidade.
Não é um requisito fazer assim.

```powershell
$roles = @{
    'CONTOSO\JEA_DNS_ADMINS'    = @{ RoleCapabilities = 'DnsAdmin', 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_OPERATORS' = @{ RoleCapabilities = 'DnsOperator', 'DnsAuditor' }
    'CONTOSO\JEA_DNS_AUDITORS'  = @{ RoleCapabilities = 'DnsAuditor' }
}

New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\JEAConfig.pssc -RunAsVirtualAccount -TranscriptDirectory 'C:\ProgramData\JEAConfiguration\Transcripts' -RoleDefinitions $roles -RequiredGroups @{ Or = '2FA-logon', 'smartcard-logon' }
Test-PSSessionConfigurationFile -Path .\JEAConfig.pssc # should yield True
```

## <a name="updating-session-configuration-files"></a>Atualizando arquivos de configuração de sessão

Se você precisar alterar as propriedades de uma configuração de sessão JEA, incluindo o mapeamento de usuários às funções, você deverá [cancelar o registro](register-jea.md#unregistering-jea-configurations) e [registrar novamente](register-jea.md) a configuração de sessão JEA.
Quando registrar novamente a configuração da sessão JEA, use um arquivo de configuração de sessão do PowerShell atualizado que inclui as alterações desejadas.

## <a name="next-steps"></a>Próximas etapas

- [Registrar uma configuração de JEA](register-jea.md)
- [Funções de autor de JEA](role-capabilities.md)
