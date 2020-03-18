---
title: Options de config à durée de couru
description: Découvrez comment configurer les applications .NET Core en utilisant des paramètres de configuration en temps d’exécution.
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399160"
---
# <a name="net-core-run-time-configuration-settings"></a>paramètres de configuration de temps d’exécution .NET Core

.NET Core prend en charge l’utilisation de fichiers de configuration et de variables de l’environnement pour configurer le comportement des applications .NET Core au moment de l’exécution. La configuration du temps d’exécution est une option intéressante si :

- Vous ne possédez pas ou ne contrôlez pas le code source d’une application et vous ne pouvez donc pas le configurer de manière programmatique.

- Plusieurs instances de votre application s’exécutent en même temps sur un seul système, et vous souhaitez configurer chacune pour des performances optimales.

> [!NOTE]
> Cette documentation est un travail en cours. Si vous remarquez que les renseignements présentés ici sont incomplets ou inexacts, soit [ouvrez une question](https://github.com/dotnet/docs/issues) pour nous le faire savoir, soit [soumettez une demande de retrait](https://github.com/dotnet/docs/pulls) pour régler le problème. Pour obtenir de [l’information](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md)sur la soumission de demandes de retrait pour le référentiel dotnet/docs, consultez le guide du contributeur .

.NET Core fournit les mécanismes suivants pour configurer le comportement d’application en temps d’exécution :

- Le [fichier runtimeconfig.json](#runtimeconfigjson)

- [Propriétés MSBuild](#msbuild-properties)

- [Variables de l’environnement](#environment-variables)

Certaines valeurs de configuration peuvent également être <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> définies programmatiquement en appelant la méthode.

Les articles de cette section de la documentation sont organisés par catégorie, par exemple, [le débogage](debugging-profiling.md) et [la collecte des ordures](garbage-collector.md). Le cas échéant, les options de configuration sont affichées pour les fichiers *runtimeconfig.json,* les propriétés MSBuild, les variables de l’environnement et, pour les fichiers *app.config* de référence croisées pour les projets cadre .NET.

## <a name="runtimeconfigjson"></a>runtimeconfig.json

Lorsqu’un projet est [construit,](../tools/dotnet-build.md)un fichier *[appname].runtimeconfig.json* est généré dans l’annuaire de sortie. Si un fichier *runtimeconfig.template.json* existe dans le même dossier que le fichier de projet, toutes les options de configuration qu’il contient sont fusionnées dans le fichier *[appname].runtimeconfig.json.* Si vous construisez l’application vous-même, placez toutes les options de configuration dans le fichier *runtimeconfig.template.json.* Si vous êtes juste en cours d’exécution de l’application, les insérer directement dans le *fichier [appname].runtimeconfig.json.*

> [!NOTE]
> Le *fichier [appname].runtimeconfig.json* sera écrasé sur les builds suivants.

Spécifier les options de configuration en temps d’exécution dans la section **configProperties** des fichiers *runtimeconfig.json.* Cette section a le formulaire:

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>Exemple [appname].runtimeconfig.json fichier

Si vous placez les options dans le fichier de `runtimeOptions` sortie JSON, entrez-les sous la propriété.

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

### <a name="example-runtimeconfigtemplatejson-file"></a>Exemple de fichier runtimeconfig.template.json

Si vous placez les options dans le fichier `runtimeOptions` JSON modèle, omettre la propriété.

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

Certaines options de configuration en temps d’exécution peuvent être définies à l’aide de propriétés MSBuild dans le fichier *.csproj* ou *.vbproj* des projets .NET Core de style SDK. Les propriétés MSBuild ont préséance sur les options définies dans le fichier *runtimeconfig.template.json.* Ils surcrivent également toutes les options que vous définissez dans le *fichier [appname].runtimeconfig.json* au moment de la construction.

Voici un exemple de fichier de projet de type SDK avec des propriétés MSBuild pour configurer le comportement en temps de course :

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

MsBuild propriétés pour configurer le comportement de temps de course sont notés dans les articles individuels pour chaque zone, par exemple, [la collecte des ordures](garbage-collector.md).

## <a name="environment-variables"></a>Variables d'environnement

Les variables de l’environnement peuvent être utilisées pour fournir des informations de configuration en temps de course. Les boutons de configuration spécifiés comme variables d’environnement ont généralement le préfixe **COMPlus_**.

Vous pouvez définir les variables de l’environnement à partir du panneau <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> de contrôle Windows, à la ligne de commande, ou de manière programmatique en appelant la méthode sur les systèmes Windows et Unix.

Les exemples suivants montrent comment définir une variable d’environnement à la ligne de commande :

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
