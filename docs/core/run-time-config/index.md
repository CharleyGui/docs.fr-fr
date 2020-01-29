---
title: Options de configuration au moment de l’exécution
description: Découvrez comment configurer des applications .NET Core à l’aide des paramètres de configuration de l’exécution.
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733438"
---
# <a name="net-core-run-time-configuration-settings"></a>Paramètres de configuration du Runtime .NET Core

.NET Core prend en charge l’utilisation de fichiers de configuration et de variables d’environnement pour configurer le comportement des applications .NET Core au moment de l’exécution. La configuration au moment de l’exécution est une option attrayante dans les cas suivants :

- Vous ne possédez pas ou ne contrôlez pas le code source d’une application. par conséquent, vous ne pouvez pas le configurer par programme.

- Plusieurs instances de votre application s’exécutent en même temps sur un système unique et vous souhaitez configurer chacune d’elles pour obtenir des performances optimales.

> [!NOTE]
> Cette documentation est un travail en cours. Si vous remarquez que les informations présentées ici sont incomplètes ou inexactes, vous pouvez soit [ouvrir un problème](https://github.com/dotnet/docs/issues) pour nous le faire savoir, soit [soumettre une demande de tirage](https://github.com/dotnet/docs/pulls) pour résoudre le problème. Pour plus d’informations sur l’envoi de requêtes de tirage pour le dépôt dotnet/docs, consultez le [Guide du contributeur](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).

.NET Core fournit les mécanismes suivants pour configurer le comportement de l’application au moment de l’exécution :

- Le [fichier runtimeconfig. JSON](#runtimeconfigjson)

- [Propriétés MSBuild](#msbuild-properties)

- [Variables d’environnement](#environment-variables)

Certaines valeurs de configuration peuvent également être définies par programmation en appelant la méthode <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.

Les Articles de cette section de la documentation sont organisés par catégorie, par exemple, [débogage](debugging-profiling.md) et [garbage collection](garbage-collector.md). Le cas échéant, des options de configuration s’affichent pour les fichiers *runtimeconfig. JSON* , les propriétés MSBuild, les variables d’environnement et, pour les références croisées, les fichiers *app. config* pour les projets .NET Framework.

## <a name="runtimeconfigjson"></a>runtimeconfig. JSON

Lorsqu’un projet est [généré](../tools/dotnet-build.md), un fichier *[AppName]. runtimeconfig. JSON* est généré dans le répertoire de sortie. Si un fichier *runtimeconfig. template. JSON* se trouve dans le même dossier que le fichier projet, toutes les options de configuration qu’il contient sont fusionnées dans le fichier *[AppName]. runtimeconfig. JSON* . Si vous créez l’application vous-même, placez toutes les options de configuration dans le fichier *runtimeconfig. template. JSON* . Si vous exécutez simplement l’application, insérez-la directement dans le fichier *[AppName]. runtimeconfig. JSON* .

> [!NOTE]
> Le fichier *[AppName]. runtimeconfig. JSON* sera remplacé lors des builds suivantes.

Spécifiez les options de configuration au moment de l’exécution dans la section **configProperties** des fichiers *runtimeconfig. JSON* . Cette section se présente sous la forme suivante :

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>Exemple de fichier [AppName]. runtimeconfig. JSON

Si vous placez les options dans le fichier JSON de sortie, imbriquez-les sous la propriété `runtimeOptions`.

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

### <a name="example-runtimeconfigtemplatejson-file"></a>Exemple de fichier runtimeconfig. template. JSON

Si vous placez les options dans le fichier JSON du modèle, omettez la propriété `runtimeOptions`.

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

Certaines options de configuration au moment de l’exécution peuvent être définies à l’aide des propriétés MSBuild dans le fichier *. csproj* ou *. vbproj* des projets .net Core de type SDK. Les propriétés MSBuild sont prioritaires sur les options définies dans le fichier *runtimeconfig. template. JSON* . Elles remplacent également toutes les options que vous définissez dans le fichier *[AppName]. runtimeconfig. JSON* au moment de la génération.

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

Les propriétés MSBuild pour la configuration du comportement au moment de l’exécution sont indiquées dans les articles individuels pour chaque zone, par exemple, [garbage collection](garbage-collector.md).

## <a name="environment-variables"></a>Variables d'environnement

Les variables d’environnement peuvent être utilisées pour fournir des informations de configuration au moment de l’exécution. Les boutons de configuration spécifiés en tant que variables d’environnement ont généralement le préfixe **COMPlus_** .

Vous pouvez définir des variables d’environnement à partir du panneau de configuration Windows, à partir de la ligne de commande ou par programme, en appelant la méthode <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> sur les systèmes Windows et UNIX.

Les exemples suivants montrent comment définir une variable d’environnement sur la ligne de commande :

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
