---
title: Outils de l’interface de ligne de commande (CLI) de .NET Core
description: Présentation des outils et fonctionnalités de l’interface de ligne de commande (CLI) de .NET Core.
ms.date: 08/14/2017
ms.openlocfilehash: f19dcb19fb9d0203b3d3795c3fdc0b026c4c60e3
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163213"
---
# <a name="net-core-command-line-interface-cli-tools"></a>Outils de l’interface de ligne de commande (CLI) de .NET Core

L’interface de ligne de commande (CLI) .NET Core est un chaîne d’outils multiplateforme pour le développement d’applications .NET. L’interface CLI est un fondement sur lequel les outils de niveau supérieur, tels que les environnements de développement intégré (IDE), les éditeurs et les orchestrateurs de build, peuvent Rest.

## <a name="installation"></a>Installation de

Utilisez les programmes d’installation natifs ou les scripts shell d’installation :

- Les programmes d’installation natifs sont principalement utilisés sur les ordinateurs des développeurs et s’appuient sur le mécanisme d’installation natif de chaque plateforme prise en charge, par exemple des packages DEB sur Ubuntu ou des ensembles MSI sur Windows. Ces programmes d’installation installent et configurent l’environnement pour une utilisation immédiate par le développeur, mais requièrent des privilèges d’administrateur sur l’ordinateur. Vous pouvez consulter les instructions d’installation dans le [guide d’installation de .NET Core](https://aka.ms/dotnetcoregs).
- Les scripts de shell servent principalement à configurer les serveurs de builds et permettent d’installer les outils sans privilèges d’administration. Les scripts d’installation n’installent pas les composants requis sur l’ordinateur, qui doivent être installés manuellement. Pour plus d’informations, consultez la [rubrique de référence sur les scripts d’installation](dotnet-install-script.md). Pour plus d’informations sur la configuration de l’interface CLI sur votre serveur de builds avec intégration continue (CI), consultez [Utilisation du SDK et des outils .NET Core avec l’intégration continue](using-ci-with-cli.md).

Par défaut, l’interface CLI s’installe en parallèle (SxS) et plusieurs versions des outils CLI peuvent donc coexister sur un même ordinateur. La méthode permettant d’identifier la version utilisée sur un ordinateur sur lequel plusieurs versions sont installées est expliquée plus en détail dans la section [Pilote](#driver).

## <a name="cli-commands"></a>Commandes CLI

Les commandes suivantes sont installées par défaut :

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Commandes de base**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [build](dotnet-build.md)
- [publish](dotnet-publish.md)
- [run](dotnet-run.md)
- [test](dotnet-test.md)
- [vstest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [migrate](dotnet-migrate.md)
- [clean](dotnet-clean.md)
- [sln](dotnet-sln.md)
- [help](dotnet-help.md)
- [store](dotnet-store.md)

**Commandes de modification de projets**

- [add package](dotnet-add-package.md)
- [add reference](dotnet-add-reference.md)
- [remove package](dotnet-remove-package.md)
- [remove reference](dotnet-remove-reference.md)
- [list reference](dotnet-list-reference.md)

**Commandes avancées**

- [nuget delete](dotnet-nuget-delete.md)
- [nuget locals](dotnet-nuget-locals.md)
- [nuget push](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [dotnet install script](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Commandes de base**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [build](dotnet-build.md)
- [publish](dotnet-publish.md)
- [run](dotnet-run.md)
- [test](dotnet-test.md)
- [vstest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [migrate](dotnet-migrate.md)
- [clean](dotnet-clean.md)
- [sln](dotnet-sln.md)

**Commandes de modification de projets**

- [add package](dotnet-add-package.md)
- [add reference](dotnet-add-reference.md)
- [remove package](dotnet-remove-package.md)
- [remove reference](dotnet-remove-reference.md)
- [list reference](dotnet-list-reference.md)

**Commandes avancées**

- [nuget delete](dotnet-nuget-delete.md)
- [nuget locals](dotnet-nuget-locals.md)
- [nuget push](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [dotnet install script](dotnet-install-script.md)

---

L’interface CLI adopte un modèle d’extensibilité qui vous permet de spécifier des outils supplémentaires pour vos projets. Pour plus d’informations, consultez la rubrique [Modèle d’extensibilité des outils CLI .NET Core](extensibility.md).

## <a name="command-structure"></a>Structure de commande

La structure de commande CLI se compose du [pilote (« dotnet »)](#driver), de la [commande](#command) et éventuellement des [arguments](#arguments) et [options](#options) de la commande. Ce modèle apparaît dans la plupart des opérations de l’interface CLI, notamment la création d’une application console et son exécution à partir de la ligne de commande, comme le montrent les commandes suivantes, exécutées à partir d’un répertoire nommé *my_app* :

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a>Pilote

Le pilote s’intitule [dotnet](dotnet.md) et gère deux tâches : l’exécution d’une [application dépendant du framework](../deploying/index.md) ou l’exécution d’une commande. 

Pour exécuter une application dépendant du framework, spécifiez l’application après le pilote, par exemple `dotnet /path/to/my_app.dll`. Lors de l’exécution de la commande à partir du dossier où se trouve la DLL de l’application, vous devez simplement exécuter `dotnet my_app.dll`. Si vous souhaitez utiliser une version spécifique de .NET Core Runtime, choisissez l’option `--fx-version <VERSION>` (voir la référence [dotnet command](dotnet.md)).

Lorsque vous fournissez une commande au pilote, `dotnet.exe` démarre le processus d’exécution de la commande CLI. Par exemple :

```dotnetcli
dotnet build
```

D’abord, le pilote détermine la version du kit SDK à utiliser. S’il n’existe pas de ['global.json'](global-json.md), la dernière version du SDK disponible est utilisée. Il s’agit peut-être d’une préversion ou d’une version stable, selon la plus récente qui se trouve sur l’ordinateur.  Une fois que la version du SDK est déterminée, elle exécute la commande.

### <a name="command"></a>Command

La commande exécute une action. Par exemple, `dotnet build` génère le code. `dotnet publish` publie le code. Les commandes sont implémentées comme une application console à l’aide d’une convention `dotnet {command}`.

### <a name="arguments"></a>Arguments

Les arguments que vous passez sur la ligne de commande sont les arguments de la commande appelée. Par exemple, lorsque vous exécutez `dotnet publish my_app.csproj`, l’argument `my_app.csproj` indique le projet à publier et est transmis à la commande `publish`.

### <a name="options"></a>Options

Les options que vous passez sur la ligne de commande sont les options de la commande appelée. Par exemple, lorsque vous exécutez `dotnet publish --output /build_output`, l’option `--output` et sa valeur sont passés à la commande `publish`.

## <a name="migration-from-projectjson"></a>Migration à partir de project.json

Si vous avez utilisé les outils Preview 2 pour produire des projets *project.json*, consultez la rubrique [dotnet migrate](dotnet-migrate.md) pour plus d’informations sur la migration de votre projet vers MSBuild/ *.csproj*. Pour les projets .NET Core créés avant la version des outils de Preview 2, mettez à jour manuellement le projet en suivant les instructions dans [Migration de DNX vers l’interface CLI .NET Core (project.json)](../migration/from-dnx.md), puis utilisez `dotnet migrate` ou mettez directement à niveau vos projets.

## <a name="see-also"></a>Voir aussi

- [Référentiel GitHub dotnet/CLI](https://github.com/dotnet/cli/)
- [Guide d’installation de .NET Core](https://aka.ms/dotnetcoregs)
