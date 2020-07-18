---
title: CLI .NET Core
titleSuffix: ''
description: Vue d’ensemble de la CLI .NET Core et de ses fonctionnalités.
ms.date: 02/13/2020
ms.openlocfilehash: f92151c85b4816fef1859e84ad94945445db1854
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86415968"
---
# <a name="net-core-cli-overview"></a>Vue d’ensemble de CLI .NET Core

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

L’interface de ligne de commande (CLI) .NET Core est un chaîne d’outils multiplateforme pour le développement, la génération, l’exécution et la publication d’applications .NET Core.

Le CLI .NET Core est inclus dans le [Kit SDK .net Core](../sdk.md). Pour savoir comment installer le kit SDK .NET Core, consultez [installer .net Core](../install/windows.md).

## <a name="cli-commands"></a>Commandes CLI

Les commandes suivantes sont installées par défaut :

### <a name="basic-commands"></a>Commandes de base

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a>Commandes de modification de projet

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a>Commandes avancées

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a>Commandes de gestion des outils

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- [`tool restore`](global-tools.md#install-a-local-tool)Disponible depuis kit SDK .NET Core 3,0.
- [`tool run`](global-tools.md#invoke-a-local-tool)Disponible depuis kit SDK .NET Core 3,0.
- [`tool uninstall`](dotnet-tool-uninstall.md)

Les outils sont des applications console qui sont installées à partir de packages NuGet et sont appelées à partir de l’invite de commandes. Vous pouvez écrire vous-même des outils ou installer des outils écrits par des tiers. Les outils sont également appelés outils globaux, outils de chemin d’accès d’outil et outils locaux. Pour plus d’informations, consultez [vue d’ensemble des outils .net Core](global-tools.md).

## <a name="command-structure"></a>Structure de commande

La structure de commande CLI se compose du [pilote (« dotnet »)](#driver), de la [commande](#command) et éventuellement des [arguments](#arguments) et [options](#options) de la commande. Ce modèle apparaît dans la plupart des opérations de l’interface CLI, notamment la création d’une application console et son exécution à partir de la ligne de commande, comme le montrent les commandes suivantes, exécutées à partir d’un répertoire nommé *my_app* :

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>Pilote

Le pilote s’intitule [dotnet](dotnet.md) et gère deux tâches : l’exécution d’une [application dépendant du framework](../deploying/index.md) ou l’exécution d’une commande.

Pour exécuter une application dépendant du framework, spécifiez l’application après le pilote, par exemple `dotnet /path/to/my_app.dll`. Lors de l’exécution de la commande à partir du dossier où se trouve la DLL de l’application, vous devez simplement exécuter `dotnet my_app.dll`. Si vous souhaitez utiliser une version spécifique de .NET Core Runtime, choisissez l’option `--fx-version <VERSION>` (voir la référence [dotnet command](dotnet.md)).

Lorsque vous fournissez une commande au pilote, `dotnet.exe` démarre le processus d’exécution de la commande CLI. Par exemple :

```dotnetcli
dotnet build
```

D’abord, le pilote détermine la version du kit SDK à utiliser. Si aucunglobal.jsn’est présent [dans](global-json.md) le fichier, la version la plus récente du kit de développement logiciel (SDK) disponible est utilisée. Il s’agit peut-être d’une préversion ou d’une version stable, selon la plus récente qui se trouve sur l’ordinateur.  Une fois que la version du SDK est déterminée, elle exécute la commande.

### <a name="command"></a>Commande

La commande exécute une action. Par exemple, `dotnet build` génère le code. `dotnet publish` publie le code. Les commandes sont implémentées comme une application console à l’aide d’une convention `dotnet {command}`.

### <a name="arguments"></a>Arguments

Les arguments que vous passez sur la ligne de commande sont les arguments de la commande appelée. Par exemple, lorsque vous exécutez `dotnet publish my_app.csproj` , l' `my_app.csproj` argument indique le projet à publier et est passé à la `publish` commande.

### <a name="options"></a>Options

Les options que vous passez sur la ligne de commande sont les options de la commande appelée. Par exemple, lorsque vous exécutez `dotnet publish --output /build_output` , l' `--output` option et sa valeur sont passées à la `publish` commande.

## <a name="see-also"></a>Voir aussi

- [référentiel GitHub dotnet/SDK](https://github.com/dotnet/sdk/)
- [Guide d’installation de .NET Core](../install/windows.md)
