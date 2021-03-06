---
title: "Comando dotnet new – CLI do .NET Core"
description: O comando dotnet new cria novos projetos .NET Core com base no modelo especificado.
keywords: dotnet-new, CLI, comando da CLI, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.workload: dotnetcore
ms.openlocfilehash: cf65dc80f135badcb1580726a12a9ae9d94ae3d7
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2018
---
# <a name="dotnet-new"></a>dotnet new

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet new` – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.

## <a name="synopsis"></a>Sinopse

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a>Descrição

O comando `dotnet new` fornece uma maneira conveniente de inicializar um projeto .NET Core válido. 

O comando chama o [mecanismo de modelo](https://github.com/dotnet/templating) para criar os artefatos em disco com base no modelo e nas opções especificadas.

## <a name="arguments"></a>Arguments

`TEMPLATE`

O modelo para o qual criar uma instância quando o comando é invocado. Cada modelo pode ter opções específicas que podem ser passadas. Para obter mais informações, consulte [Opções de modelo](#template-options).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

O comando contém uma lista padrão de modelos. Use `dotnet new -l` para obter uma lista dos modelos disponíveis. A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 2.0. O idioma padrão do modelo é mostrado entre parênteses.

|Descrição do modelo                          | Nome do modelo | Linguagens     |
|----------------------------------------------|---------------|---------------|
| Aplicativo de console                          | `console`     | [C#], F#, VB  |
| Biblioteca de classes                                | `classlib`    | [C#], F#, VB  |
| Projeto de teste de unidade                            | `mstest`      | [C#], F#, VB  |
| Projeto de teste de xUnit                           | `xunit`       | [C#], F#, VB  |
| ASP.NET Core vazio                           | `web`         | [C#], F#      |
| Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador) | `mvc`         | [C#], F#      |
| Aplicativo Web ASP.NET Core                         | `razor`       | [C#]          |
| ASP.NET Core com Angular                    | `angular`     | [C#]          |
| ASP.NET Core com React.js                   | `react`       | [C#]          |
| ASP.NET Core com React.js e Redux         | `reactredux`  | [C#]          |
| API Web do ASP.NET Core                         | `webapi`      | [C#], F#      |
| Arquivo global.json                             | `globaljson`  |               |
| Configuração do NuGet                                 | `nugetconfig` |               |
| Configuração da Web                                   | `webconfig`   |               |
| Arquivo de solução                                | `sln`         |               |
| Página do Razor                                   | `page`        |               |
| MVC/ViewImports                              | `viewimports` |               |
| MVC ViewStart                                | `viewstart`   |               |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

O comando contém uma lista padrão de modelos. Use `dotnet new -all` para obter uma lista dos modelos disponíveis. A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET Core 1.x. O idioma padrão do modelo é mostrado entre parênteses.

|Descrição do modelo  | Nome do modelo | Linguagens |
|----------------------|---------------|-----------|
| Aplicativo de console  | `console`     | [C#], F#  |
| Biblioteca de classes        | `classlib`    | [C#], F#  |
| Projeto de teste de unidade    | `mstest`      | [C#], F#  |
| Projeto de teste de xUnit   | `xunit`       | [C#], F#  |
| ASP.NET Core vazio   | `web`         | [C#]      |
| Aplicativo Web ASP.NET Core | `mvc`         | [C#], F#  |
| API Web do ASP.NET Core | `webapi`      | [C#]      |
| Configuração do NuGet         | `nugetconfig` |           |
| Configuração da Web           | `webconfig`   |           |
| Arquivo de solução        | `sln`         |           |

---

## <a name="options"></a>Opções

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`--force`

Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes. Isso é necessário quando o diretório de saída já contiver um projeto.

`-h|--help`

Imprime uma ajuda para o comando. Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.

`-i|--install <PATH|NUGET_ID>`

Instala um pacote de origem ou de modelo do `PATH` ou `NUGET_ID` fornecido. Para obter informações sobre a criação de modelos personalizados, consulte [Custom templates for dotnet new](custom-templates.md) (Modelos personalizados para dotnet new).

`-l|--list`

Lista os modelos que contêm o nome especificado. Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado. Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.

`-lang|--language {C#|F#|VB}`

A linguagem do modelo a ser criada. A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)). Não é válida para alguns modelos.

`-n|--name <OUTPUT_NAME>`

O nome para a saída criada. Se nenhum nome for especificado, o nome do diretório atual será usado.

`-o|--output <OUTPUT_DIRECTORY>`

Local para colocar a saída gerada. O padrão é o diretório atual.

`--type`

Filtra modelos com base em tipos disponíveis. Os valores predefinidos são "projeto", "item" ou "outro".

`-u|--uninstall <PATH|NUGET_ID>`

Desinstala um pacote de origem ou de modelo no `PATH` ou `NUGET_ID` fornecido.

> [!NOTE]
> Para desinstalar um modelo usando um `PATH`, você precisa qualificar totalmente o caminho. Por exemplo, *C:/Usuários/\<USUÁRIO>/Documentos/Modelos/GarciaSoftware.ConsoleTemplate.CSharp* funcionará, mas *./GarciaSoftware.ConsoleTemplate.CSharp* da pasta que o contém, não.
> Além disso, não inclua uma barra final de encerramento de diretório no caminho do modelo.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-all|--show-all`

Mostra todos os modelos de um tipo específico de projeto durante a execução no contexto do comando `dotnet new` isolado. Durante a execução no contexto de um modelo específico, como `dotnet new web -all`, `-all` é interpretado como um sinalizador de criação de força. Isso é necessário quando o diretório de saída já contiver um projeto.

`-h|--help`

Imprime uma ajuda para o comando. Ele pode ser invocado para o próprio comando `dotnet new` ou para qualquer modelo, como `dotnet new mvc --help`.

`-l|--list`

Lista os modelos que contêm o nome especificado. Se for invocado para o comando `dotnet new`, listará os possíveis modelos disponíveis para o diretório especificado. Por exemplo, se o diretório já contiver um projeto, ele não listará todos os modelos de projeto.

`-lang|--language {C#|F#}`

A linguagem do modelo a ser criada. A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção [Argumentos](#arguments)). Não é válida para alguns modelos.

`-n|--name <OUTPUT_NAME>`

O nome para a saída criada. Se nenhum nome for especificado, o nome do diretório atual será usado.

`-o|--output <OUTPUT_DIRECTORY>`

Local para colocar a saída gerada. O padrão é o diretório atual.

---

## <a name="template-options"></a>Opções de modelo

Cada modelo de projeto pode ter opções adicionais disponíveis. Os principais modelos têm as seguintes opções adicionais:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**console, angular, react, reactredux**

`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.

**classlib**

`-f|--framework <FRAMEWORK>` – especifica a qual [estrutura](../../standard/frameworks.md) se destina. Valores: `netcoreapp2.0` para criar uma Biblioteca de classes do .NET Core ou `netstandard2.0` para criar uma Biblioteca de classes .NET Standard. O valor padrão é `netstandard2.0`.

`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.

**mstest, xunit**

`-p|--enable-pack` – Habilita empacotamento para o projeto usando [dotnet pack](dotnet-pack.md).

`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.

**globaljson**

`--sdk-version <VERSION_NUMBER>` – Especifica a versão do SDK do .NET Core a ser usada no arquivo *global.json*.

**web**

`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.

`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado. Os valores possíveis são:

- `None` – Nenhuma autenticação (Padrão).
- `IndividualB2C` – Autenticação individual com o Azure AD B2C.
- `SingleOrg` – Autenticação organizacional para um único locatário.
- `Windows` – Autenticação do Windows.

`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar. Use com a autenticação do `IndividualB2C`. O valor padrão é `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto. Use com a autenticação do `IndividualB2C`.

`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar. Use com a autenticação do `SingleOrg`. O valor padrão é `https://login.microsoftonline.com/`.

`--client-id <ID>` – A ID do cliente deste projeto. Use com a autenticação `IndividualB2C` ou `SingleOrg`. O valor padrão é `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` – O domínio do locatário de diretório. Use com a autenticação `SingleOrg` ou `IndividualB2C`. O valor padrão é `qualified.domain.name`.

`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar. Use com a autenticação do `SingleOrg`. O valor padrão é `22222222-2222-2222-2222-222222222222`.

`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório. Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.

`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.

`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite. Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.

`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.

**mvc, razor**

`-au|--auth <AUTHENTICATION_TYPE>` – O tipo de autenticação usado. Os valores possíveis são:

- `None` – Nenhuma autenticação (Padrão).
- `Individual` – Autenticação individual.
- `IndividualB2C` – Autenticação individual com o Azure AD B2C.
- `SingleOrg` – Autenticação organizacional para um único locatário.
- `MultiOrg` – Autenticação organizacional para vários locatários.
- `Windows` – Autenticação do Windows.

`--aad-b2c-instance <INSTANCE>` – A instância do Azure Active Directory B2C à qual se conectar. Use com a autenticação do `IndividualB2C`. O valor padrão é `https://login.microsoftonline.com/tfp/`.

`-ssp|--susi-policy-id <ID>` – A ID da política de credenciais e de inscrição desse projeto. Use com a autenticação do `IndividualB2C`.

`-rp|--reset-password-policy-id <ID>` – A ID da política de senha de redefinição para este projeto. Use com a autenticação do `IndividualB2C`.

`-ep|--edit-profile-policy-id <ID>` – A ID da política de perfil de edição para este projeto. Use com a autenticação do `IndividualB2C`.

`--aad-instance <INSTANCE>` – A instância do Azure Active Directory à qual se conectar. Use com a autenticação `SingleOrg` ou `MultiOrg`. O valor padrão é `https://login.microsoftonline.com/`.

`--client-id <ID>` – A ID do cliente deste projeto. Use com a autenticação `IndividualB2C`, `SingleOrg` ou `MultiOrg`. O valor padrão é `11111111-1111-1111-11111111111111111`.

`--domain <DOMAIN>` – O domínio do locatário de diretório. Use com a autenticação `SingleOrg` ou `IndividualB2C`. O valor padrão é `qualified.domain.name`.

`--tenant-id <ID>` – A ID TenantId do diretório ao qual se conectar. Use com a autenticação `SingleOrg`. O valor padrão é `22222222-2222-2222-2222-222222222222`.

`--callback-path <PATH>` – O caminho da solicitação dentro do caminho base do aplicativo do URI de redirecionamento. Use com a autenticação `SingleOrg` ou `IndividualB2C`. O valor padrão é `/signin-oidc`.

`-r|--org-read-access` – Permite que esse aplicativo tenha acesso de leitura ao diretório. Aplicável apenas à autenticação `SingleOrg` ou `MultiOrg`.

`--use-launch-settings` – Inclui *launchSettings.json* na saída do modelo gerado.

`--use-browserlink` – Inclui BrowserLink no projeto.

`-uld|--use-local-db` – Especifica que LocalDB deve ser usado em vez de SQLite. Aplicável apenas à autenticação `Individual` ou `IndividualB2C`.

`--no-restore` – Não executa uma restauração implícita durante a criação do projeto.

**page**

`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado. O valor padrão é `MyApp.Namespace`.

`-np|--no-pagemodel` – Cria a página sem um PageModel.

**viewimports**

`-na|--namespace <NAMESPACE_NAME>` – Namespace do código gerado. O valor padrão é `MyApp.Namespace`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**console, xunit, mstest, web, webapi** 

`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina. Valores: `netcoreapp1.0` ou `netcoreapp1.1`. O valor padrão é `netcoreapp1.0`.

**classlib**

`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina. Valores: `netcoreapp1.0`, `netcoreapp1.1` ou `netstandard1.0` como `netstandard1.6`. O valor padrão é `netstandard1.4`.

**mvc**

`-f|--framework` – especifica a qual [estrutura](../../standard/frameworks.md) se destina. Valores: `netcoreapp1.0` ou `netcoreapp1.1`. O valor padrão é `netcoreapp1.0`.

`-au|--auth` – O tipo de autenticação usado. Valores: `None` ou `Individual`. O valor padrão é `None`.

`-uld|--use-local-db` – Especifica se deve usar ou não o LocalDB em vez do SQLite. Valores: `true` ou `false`. O valor padrão é `false`.

---

## <a name="examples"></a>Exemplos

Crie um projeto de aplicativo de console F# no diretório atual:

`dotnet new console -lang f#`

Crie um projeto de biblioteca de classes do .NET Standard no diretório especificado (disponível somente com o SDK do .NET Core 2.0 ou versões posteriores):

`dotnet new classlib -lang VB -o MyLibrary`

Crie um novo projeto de aplicativo de MVC C# do ASP.NET Core no diretório atual sem autenticação direcionando o .NET Core 2.0:

`dotnet new mvc -au None -f netcoreapp2.0`

Crie um novo aplicativo xUnit direcionando o .NET Core 2.0:

`dotnet new xunit --framework netcoreapp2.0`

Lista todos os modelos disponíveis para o MVC:

`dotnet new mvc -l`

## <a name="see-also"></a>Consulte também

[Modelos personalizados para dotnet new](custom-templates.md)  
[Create a custom template for dotnet new](~/docs/core/tutorials/create-custom-template.md) (Criar um modelo personalizado para dotnet new)  
[Repositório do GitHub de dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples)  
[Modelos disponíveis para dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)
