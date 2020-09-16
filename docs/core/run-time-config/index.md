---
title: Options de configuration au moment de l’exécution
description: Découvrez comment configurer des applications .NET Core à l’aide des paramètres de configuration de l’exécution.
ms.date: 01/21/2020
ms.openlocfilehash: 21673a221d0f21202febf4730b955da66132d5f7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538196"
---
# <a name="net-core-run-time-configuration-settings"></a>Paramètres de configuration du Runtime .NET Core

.NET Core prend en charge l’utilisation de fichiers de configuration et de variables d’environnement pour configurer le comportement des applications .NET Core au moment de l’exécution. La configuration au moment de l’exécution est une option attrayante dans les cas suivants :

- Vous ne possédez pas ou ne contrôlez pas le code source d’une application. par conséquent, vous ne pouvez pas le configurer par programme.

- Plusieurs instances de votre application s’exécutent en même temps sur un système unique et vous souhaitez configurer chacune d’elles pour obtenir des performances optimales.

> [!NOTE]
> Cette documentation est un travail en cours. Si vous remarquez que les informations présentées ici sont incomplètes ou inexactes, vous pouvez soit [ouvrir un problème](https://github.com/dotnet/docs/issues) pour nous le faire savoir, soit [soumettre une demande de tirage](https://github.com/dotnet/docs/pulls) pour résoudre le problème. Pour plus d’informations sur l’envoi de requêtes de tirage pour le dépôt dotnet/docs, consultez le [Guide du contributeur](/contribute/dotnet/dotnet-contribute).

.NET Core fournit les mécanismes suivants pour configurer le comportement de l’application au moment de l’exécution :

- [runtimeconfig.jssur le fichier](#runtimeconfigjson)

- [MSBuild (propriétés)](#msbuild-properties)

- [Variables d’environnement](#environment-variables)

> [!TIP]
> La configuration d’une option au moment de l’exécution à l’aide d’une variable d’environnement applique le paramètre à toutes les applications .NET Core. La configuration d’une option au moment de l’exécution dans le fichier * deruntimeconfig.jsou sur* le fichier projet applique le paramètre à cette application uniquement.

Certaines valeurs de configuration peuvent également être définies par programmation en appelant la <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> méthode.

Les Articles de cette section de la documentation sont organisés par catégorie, par exemple, [débogage](debugging-profiling.md) et [garbage collection](garbage-collector.md). Le cas échéant, des options de configuration s’affichent pour *runtimeconfig.jssur* les fichiers, les propriétés MSBuild, les variables d’environnement et, pour les références croisées, les fichiers *app.config* pour les projets .NET Framework.

## <a name="runtimeconfigjson"></a>runtimeconfig.js

Lorsqu’un projet est [généré](../tools/dotnet-build.md), une *.runtimeconfig.js[AppName] sur* le fichier est générée dans le répertoire de sortie. Si un *runtimeconfig.template.jssur* le fichier existe dans le même dossier que le fichier projet, toutes les options de configuration qu’il contient sont fusionnées dans le fichier *[AppName] .runtimeconfig.js* . Si vous créez l’application vous-même, placez toutes les options de configuration dans le *runtimeconfig.template.js* fichier. Si vous exécutez simplement l’application, insérez-la directement dans le fichier *[AppName] .runtimeconfig.js* .

> [!NOTE]
> Le *.runtimeconfig.js[AppName] sur* le fichier sera remplacé lors des builds suivantes.

Spécifiez les options de configuration au moment de l’exécution dans la section **configProperties** du *runtimeconfig.jssur* les fichiers. Cette section se présente sous la forme suivante :

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>Exemple [AppName] .runtimeconfig.jssur le fichier

Si vous placez les options dans le fichier JSON de sortie, imbriquez-les sous la `runtimeOptions` propriété.

```json
{
  "runtimeOptions": {
    "tfm": "netcoreapp3.1",
    "framework": {
      "name": "Microsoft.NETCore.App",
      "version": "3.1.0"
    },
    "configProperties": {
      "System.GC.Concurrent": false,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

### <a name="example-runtimeconfigtemplatejson-file"></a>Exemple de runtimeconfig.template.jssur un fichier

Si vous placez les options dans le fichier JSON du modèle, omettez la `runtimeOptions` propriété.

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a>MSBuild (propriétés)

Certaines options de configuration au moment de l’exécution peuvent être définies à l’aide des propriétés MSBuild dans le fichier *. csproj* ou *. vbproj* des projets .net Core de type SDK. Les propriétés MSBuild sont prioritaires sur les options définies dans le *runtimeconfig.template.jssur* le fichier. Elles remplacent également toutes les options que vous définissez dans le *.runtimeconfig.js[AppName]* au moment de la génération.

Voici un exemple de fichier projet de type SDK avec des propriétés MSBuild pour la configuration du comportement au moment de l’exécution :

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
    <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```

Les propriétés MSBuild pour la configuration du comportement au moment de l’exécution sont indiquées dans les articles individuels pour chaque zone, par exemple, [garbage collection](garbage-collector.md). Ils sont également répertoriés dans la section Configuration de l' [exécution](../project-sdk/msbuild-props.md#run-time-configuration-properties) de la référence des propriétés MSBuild pour les projets de type SDK.

## <a name="environment-variables"></a>Variables d'environnement

Les variables d’environnement peuvent être utilisées pour fournir des informations de configuration au moment de l’exécution. La configuration d’une option au moment de l’exécution à l’aide d’une variable d’environnement applique le paramètre à toutes les applications .NET Core. Les boutons de configuration spécifiés en tant que variables d’environnement ont généralement le préfixe **COMPlus_**.

Vous pouvez définir des variables d’environnement à partir du panneau de configuration Windows, à partir de la ligne de commande ou par programme, en appelant la <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> méthode sur les systèmes Windows et UNIX.

Les exemples suivants montrent comment définir une variable d’environnement sur la ligne de commande :

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
