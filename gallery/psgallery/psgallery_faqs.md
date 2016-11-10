---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, cmdlet, galeria
ms.date: 2016-10-14
contributor: manikb
title: psgallery_faqs
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 96d38c487a311852a0f670b7d3de4929fab68e4d

---

# perguntas frequentes

## O que é um módulo do PowerShell?

Um módulo do PowerShell é um pacote reutilizável que contém algumas funcionalidades do PowerShell. Tudo no PowerShell (funções, variáveis, recursos de DSC etc.) pode ser empacotado em módulos. Normalmente, os módulos são pastas que contêm tipos específicos de arquivos armazenados em um caminho específico. Há alguns tipos diferentes de módulos do PowerShell por aí.

## O que é um script do PowerShell?

Um script do PowerShell é uma série de comandos que são armazenados em um arquivo .ps1 para habilitar o compartilhamento e a reutilização. Fluxos de trabalho do PowerShell também são scripts do PowerShell, que descrevem um conjunto de tarefas e fornecem o sequenciamento dessas tarefas. Para obter mais informações, visite [Introdução ao fluxo de trabalho do PowerShell](https://technet.microsoft.com/en-us/library/jj134242.aspx).

## Qual é a diferença entre os scripts e os módulos do PowerShell?

Normalmente, os módulos são melhores para compartilhamento, mas nós estamos habilitando o compartilhamento de scripts para facilitar que você contribua com fluxos de trabalho e scripts para a comunidade. Para obter mais informações, consulte os blogs a seguir:

- [Don't Write Scripts, Write PowerShell Modules (Não escreva scripts, escreva módulos do PowerShell)](http://blogs.technet.com/b/heyscriptingguy/archive/2011/06/27/don-t-write-scripts-write-powershell-modules.aspx)
- [Understanding PowerShell Modules (Entendendo os módulos do PowerShell)](http://blogs.technet.com/b/heyscriptingguy/archive/2015/07/10/understanding-powershell-modules.aspx)

## How can I publish to the PowerShell Gallery? (Como publicar na Galeria do PowerShell?)

Você precisa registrar uma conta na Galeria do PowerShell antes que possa publicar itens na Galeria. Isso ocorre porque a publicação de itens requer uma NuGetApiKey, que é fornecida no registro. Para se registrar, use sua conta pessoal, corporativa ou de estudante para entrar na Galeria do PowerShell. Um processo de registro único é necessário quando você entra pela primeira vez. Posteriormente, a NuGetApiKey fica disponível em sua página de perfil.

Após ter se registrado na Galeria, use os cmdlets [Publish-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ou [Publish-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) para publicar seu item na Galeria. Para obter mais detalhes sobre como executar esses cmdlets, visite a guia Publicar ou leia a documentação sobre [Publish-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [Publish-Script](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

**Você não precisa se registrar ou entrar na Galeria para instalar ou salvar itens.**

## Recebi o erro "Falha ao processar solicitação. A chave de API especificada é inválida ou não tem permissão para acessar o pacote especificado. O servidor remoto retornou um erro: (403) Proibido." ao tentar publicar um item na Galeria do PowerShell. O que isso significa?

Esse erro pode ocorrer por um dos seguintes motivos:

- **A chave de API especificada é inválida.**
     Confirme se você especificou a chave de API válida de sua conta. Para obter sua chave de API, exiba sua página de perfil.
- **O nome do item especificado não pertence a você.**
     Se você tiver confirmado que a chave de API está correta, talvez já exista um item com o mesmo nome do que você está tentando usar. O item pode ter sido removido da lista pelo proprietário. Nesse caso, ele não será exibido nos resultados da pesquisa. Para determinar se um item com o mesmo nome já existe, abra um navegador e navegue até a página de detalhes do item: `https://www.powershellgallery.com/packages/<itemName>`. Por exemplo, navegar diretamente até `https://www.powershellgallery.com/packages/pester` levará você à página de detalhes do módulo Pester, quer ele seja removido da lista ou não. Se um item com um nome conflitante já existir e não estiver listado, você poderá:
    - selecionar outro nome para o item.
    - entrar em contato com os proprietários do item existente.

## Por que não posso entrar com minha conta pessoal, mas podia entrar ontem?

Esteja ciente de que sua conta da Galeria não acomoda alterações no seu alias do email principal. Para obter mais informações, consulte [Aliases de Email da Microsoft](http://windows.microsoft.com/en-us/windows/outlook/add-alias-account).

## Por que não vejo todos os itens da Galeria quando marco todas as caixas de seleção de Categoria na guia Itens?

Quando marca uma caixa de seleção de Categoria, você está dizendo "Eu gostaria de ver todos os itens desta categoria." Somente os itens das categorias selecionadas serão exibidos. De forma semelhante, quando marca todas as caixas de seleção de Categoria, você está dizendo "Eu gostaria de ver todos os itens de todas as categorias." Mas alguns itens da Galeria não pertencem a nenhuma das categorias listadas, de modo que eles não aparecerão nos resultados. Para ver todos os itens da Galeria, desmarque todas as Categorias ou selecione a guia Itens novamente.

## Quais são os requisitos para publicar um módulo na Galeria do PowerShell?

Qualquer tipo de módulo do PowerShell (módulos de script, módulos binários ou módulos de manifesto) pode ser publicado na Galeria. Para publicar um módulo, o PowerShellGet precisa saber algumas coisas sobre ele – a versão, a descrição, o autor e como ele está licenciado. Essas informações são lidas como parte do processo de publicação do *manifesto do módulo* arquivo (.psd1) ou do valor do parâmetro [**LicenseUri**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) do cmdlet **Publish-Module**. Todos os módulos publicados na Galeria devem ter manifestos de módulo. Qualquer módulo que incluir as seguintes informações em seu manifesto pode ser publicado na Galeria:

- Versão
- Descrição
- Autor
- Um URI para os termos de licença do módulo, como parte da seção **PrivateData** do manifesto ou no parâmetro **LicenseUri** do cmdlet [**Publish-Module**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

## Como posso criar um manifesto de módulo formatado corretamente?

A maneira mais fácil de criar um manifesto de módulo é executar o cmdlet [**New-ModuleManifest**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). No PowerShell 5.0 ou mais recente, New-ModuleManifest gera um manifesto de módulo formatado corretamente com campos em branco para metadados úteis, como **ProjectUri**, **LicenseUri** e **Tags**. Basta preencher os espaços em branco ou usar o manifesto gerado como um exemplo da formatação correta.

Para verificar se todos os campos de metadados obrigatórios foram preenchidos corretamente, use o cmdlet [**Test-ModuleManifest**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

Para atualizar os campos do arquivo de manifesto do módulo, use o cmdlet [**Update-ModuleManifest**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

## Quais são os requisitos para publicar um script na Galeria?

Qualquer tipo de script do PowerShell (scripts ou fluxos de trabalho) pode ser publicado na Galeria. Para publicar um script, o PowerShellGet precisa saber algumas coisas sobre ele – a versão, a descrição, o autor e como ele está licenciado. Essas informações são lidas como parte do processo de publicação da seção *PSScriptInfo* do arquivo de script ou do valor do parâmetro [**LicenseUri**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) do cmdlet **Publish-Script**. Todos os scripts publicados na Galeria devem ter informações dos metadados. Qualquer script que incluir as seguintes informações em sua seção PSScriptInfo pode ser publicado na Galeria:

- Versão
- Descrição
- Autor
- Um URI para os termos de licença do script, como parte da seção **PSScriptInfo** do manifesto ou no parâmetro **LicenseUri** do cmdlet [**Publish-Script**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

## Como pesquisar?

Digite o que você está procurando na caixa de texto. Por exemplo, se quiser localizar os módulos relacionados ao SQL do Azure, basta digitar "azure sql". Nosso mecanismo de pesquisa procurará por essas palavras-chave em todos os itens publicados, inclusive nos títulos, descrições e metadados. Em seguida, com base em uma pontuação de qualidade ponderada, ele exibirá as correspondências mais próximas. Você também pode pesquisar por um campo específico usando a sintaxe campo: "valor" na consulta de pesquisa para os seguintes campos:

- Marcas
- Funções
- Cmdlets
- DscResources
- PowerShellVersion

Portanto, por exemplo, quando você pesquisa PowerShellVersion: "2.0", apenas os resultados compatíveis com o PowerShellVersion 2.0 (com base em seu manifesto de módulo/script) serão exibidos.

## Como posso criar um arquivo de script formatado corretamente?

A maneira mais fácil de criar um arquivo de script formatado corretamente é executar o cmdlet [**New-ScriptFileInfo**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409). No PowerShell 5.0, New-ScriptFileInfo gera um arquivo de script formatado corretamente com campos em branco para metadados úteis, como **ProjectUri**, **LicenseUri** e **Tags**. Basta preencher os espaços em branco ou usar o arquivo de script gerado como um exemplo da formatação correta.

Para verificar se todos os campos de metadados obrigatórios foram preenchidos corretamente, use o cmdlet [**Test-ScriptFileInfo**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

Para atualizar os campos de metadados do script, use o cmdlet [**Update-ScriptFileInfo**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

## Quais outros tipos de módulos do PowerShell existem?

O termo módulo do PowerShell também se refere aos arquivos que implementam a funcionalidade real. Arquivos de módulo de script (.psm1) contêm código do PowerShell. Arquivos de módulo binários (.dll) contêm código compilado.

Esta é uma forma de pensar neles: a pasta que encapsula o módulo é a pasta de módulo. A pasta de módulo pode conter um manifesto de módulo (.psd1) que descreve o conteúdo da pasta. Os arquivos que realmente fazem o trabalho são os arquivos de módulo de script (.psm1) e os arquivos de módulo binário (.dll). Os recursos de DSC ficam localizados em uma subpasta específica e são implementados como arquivos de módulo de script ou de módulo binário.

Todos os módulos na Galeria contêm manifestos de módulo e a maioria desses módulos contêm arquivos de módulo de script ou módulo binário. O termo módulo pode ser confuso devido a esses significados diferentes. A menos que seja indicado explicitamente o contrário, todos os usos da palavra módulo nesta página fazem referência à pasta de módulo que contém esses arquivos.

## Como PackageManagement está relacionado ao PowerShellGet? (Resposta de alto nível)

PackageManagement é uma interface comum para trabalhar com qualquer gerenciador de pacotes. Quer esteja lidando com módulos do PowerShell, MSIs, RubyGems, pacotes do NuGet ou módulos do Perl, você deve ser capaz de usar comandos do PackageManagement (Find-Package e Install-Package) para localizar e instalá-los. PackageManagement faz isso tendo um provedor de pacote para cada gerenciador de pacotes que se conecta a ele. Os provedores fazem todo o trabalho real; eles buscam o conteúdo de repositórios e instalam o conteúdo localmente. Frequentemente, os provedores de pacote simplesmente encapsulam as ferramentas do gerenciador de pacotes existente para um determinado tipo de pacote.

PowerShellGet é o gerenciador de pacotes de itens do PowerShell. Há um provedor de pacotes PSModule que expõe a funcionalidade do PowerShellGet por meio de PackageManagement. Por isso, é possível executar [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) ou Install-Package -Provider PSModule para instalar um módulo na Galeria do PowerShell. Algumas funcionalidades do PowerShellGet, incluindo [Update-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) e [Publish-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409), não podem ser acessadas por meio de comandos do PackageManagement.

Em resumo, o PowerShellGet destina-se unicamente a ter uma experiência de gerenciamento de pacotes premium para o conteúdo do PowerShell. PackageManagement destina-se a expor todas as experiências de gerenciamento de pacotes por meio de um conjunto de ferramentas geral. Se você considerar esta resposta insatisfatória, haverá uma resposta longa na parte inferior deste documento, na seção **Como PackageManagement de fato está relacionado ao PowerShellGet?**.

Para obter mais informações, visite a [página do projeto do PackageManagement](http://oneget.org/).

## Como o NuGet está relacionado ao PowerShellGet?

A Galeria do PowerShell é uma versão modificada da [Galeria do NuGet](http://www.nuget.org/). O PowerShellGet usa o provedor do NuGet para trabalhar com repositórios baseados em NuGet, como a Galeria do PowerShell.

Você pode usar o PowerShellGet com qualquer compartilhamento de arquivo ou repositório do NuGet válido. Basta adicionar o repositório executando o cmdlet [**Register-PSRepository**](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409).

## Isso significa que posso usar NuGet.exe para trabalhar com a Galeria?

Sim.

## Como PackageManagement de fato está relacionado ao PowerShellGet? (Detalhes técnicos)

Nos bastidores, o PowerShellGet utiliza intensamente a infraestrutura de PackageManagement.

Na camada de cmdlet do PowerShell, [Install-Module](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) é, na verdade, um wrapper fino ao redor de Install-Package -Provider PSModule.

Na camada do provedor do pacote PackageManagement, o provedor de pacote PSModule chama outros provedores do pacote PackageManagement. Por exemplo, quando você está trabalhando com galerias baseadas em NuGet (como a Galeria do PowerShell), o provedor do pacote PSModule usa o provedor de pacote do NuGet para trabalhar com o repositório.

![Arquitetura do PowerShellGet](Images/powershellgetArchitecture.png)

Figura 1: Arquitetura do PowerShellGet

## O que é necessário para executar o PowerShellGet?

De modo geral, é recomendável escolher a versão mais recente do módulo PowerShellGet (observe que ele requer o .NET 4.5).

O módulo **PowerShellGet** exige o **PowerShell 3.0 ou mais recente**.

Portanto, **PowerShellGet** exige um dos seguintes sistemas operacionais:

- Windows 10
- Windows 8.1 Pro
- Windows 8.1 Enterprise
- Windows 7 SP1
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2008 R2 SP1

**PowerShellGet** também exige o .NET Framework 4.5 ou posterior. Você pode instalar o .NET Framework 4.5 ou acima acessando [aqui](https://msdn.microsoft.com/en-us/library/5a4x27ek.aspx).

## É possível reservar nomes para itens que serão publicados no futuro?

Não é possível guardar nomes de itens. Se você acreditar que um item existente está usando um nome que seria mais adequado para o seu item, tente [entrar em contato com o proprietário do item](psgallery_contacting_item_owners.md). Se não receber uma resposta dentro de duas semanas, você poderá contatar o suporte e a equipe da Galeria do PowerShell examinará a questão.

## Como declarar a propriedade de itens?

Confira [Gerenciando proprietários do item em PowerShellGallery.com](Managing-Item-Owners.md) para obter detalhes.

## Como lidar com um proprietário de item que está violando a licença do meu item?

Recomendamos que a comunidade do PowerShell trabalhe junta para resolver controvérsias que podem surgir entre os proprietários dos itens.  Nós criamos um [processo de solução de controvérsias](psgallery_dispute_resolution.md) e solicitamos que você o siga antes que os administradores do PowerShellGallery.com intercedam.




<!--HONumber=Oct16_HO2-->

