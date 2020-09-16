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
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="2c76d-103">Paramètres de configuration du Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="2c76d-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="2c76d-104">.NET Core prend en charge l’utilisation de fichiers de configuration et de variables d’environnement pour configurer le comportement des applications .NET Core au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2c76d-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="2c76d-105">La configuration au moment de l’exécution est une option attrayante dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="2c76d-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="2c76d-106">Vous ne possédez pas ou ne contrôlez pas le code source d’une application. par conséquent, vous ne pouvez pas le configurer par programme.</span><span class="sxs-lookup"><span data-stu-id="2c76d-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="2c76d-107">Plusieurs instances de votre application s’exécutent en même temps sur un système unique et vous souhaitez configurer chacune d’elles pour obtenir des performances optimales.</span><span class="sxs-lookup"><span data-stu-id="2c76d-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="2c76d-108">Cette documentation est un travail en cours.</span><span class="sxs-lookup"><span data-stu-id="2c76d-108">This documentation is a work in progress.</span></span> <span data-ttu-id="2c76d-109">Si vous remarquez que les informations présentées ici sont incomplètes ou inexactes, vous pouvez soit [ouvrir un problème](https://github.com/dotnet/docs/issues) pour nous le faire savoir, soit [soumettre une demande de tirage](https://github.com/dotnet/docs/pulls) pour résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="2c76d-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="2c76d-110">Pour plus d’informations sur l’envoi de requêtes de tirage pour le dépôt dotnet/docs, consultez le [Guide du contributeur](/contribute/dotnet/dotnet-contribute).</span><span class="sxs-lookup"><span data-stu-id="2c76d-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](/contribute/dotnet/dotnet-contribute).</span></span>

<span data-ttu-id="2c76d-111">.NET Core fournit les mécanismes suivants pour configurer le comportement de l’application au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="2c76d-111">.NET Core provides the following mechanisms for configuring application behavior at run time:</span></span>

- <span data-ttu-id="2c76d-112">[runtimeconfig.jssur le fichier](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="2c76d-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="2c76d-113">MSBuild (propriétés)</span><span class="sxs-lookup"><span data-stu-id="2c76d-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="2c76d-114">Variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="2c76d-114">Environment variables</span></span>](#environment-variables)

> [!TIP]
> <span data-ttu-id="2c76d-115">La configuration d’une option au moment de l’exécution à l’aide d’une variable d’environnement applique le paramètre à toutes les applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2c76d-115">Configuring a run-time option by using an environment variable applies the setting to all .NET Core apps.</span></span> <span data-ttu-id="2c76d-116">La configuration d’une option au moment de l’exécution dans le fichier \* deruntimeconfig.jsou sur\* le fichier projet applique le paramètre à cette application uniquement.</span><span class="sxs-lookup"><span data-stu-id="2c76d-116">Configuring a run-time option in the *runtimeconfig.json* or project file applies the setting to that application only.</span></span>

<span data-ttu-id="2c76d-117">Certaines valeurs de configuration peuvent également être définies par programmation en appelant la <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="2c76d-117">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="2c76d-118">Les Articles de cette section de la documentation sont organisés par catégorie, par exemple, [débogage](debugging-profiling.md) et [garbage collection](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="2c76d-118">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="2c76d-119">Le cas échéant, des options de configuration s’affichent pour *runtimeconfig.jssur* les fichiers, les propriétés MSBuild, les variables d’environnement et, pour les références croisées, les fichiers *app.config* pour les projets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c76d-119">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="2c76d-120">runtimeconfig.js</span><span class="sxs-lookup"><span data-stu-id="2c76d-120">runtimeconfig.json</span></span>

<span data-ttu-id="2c76d-121">Lorsqu’un projet est [généré](../tools/dotnet-build.md), une *.runtimeconfig.js[AppName] sur* le fichier est générée dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="2c76d-121">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="2c76d-122">Si un *runtimeconfig.template.jssur* le fichier existe dans le même dossier que le fichier projet, toutes les options de configuration qu’il contient sont fusionnées dans le fichier *[AppName] .runtimeconfig.js* .</span><span class="sxs-lookup"><span data-stu-id="2c76d-122">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="2c76d-123">Si vous créez l’application vous-même, placez toutes les options de configuration dans le *runtimeconfig.template.js* fichier.</span><span class="sxs-lookup"><span data-stu-id="2c76d-123">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="2c76d-124">Si vous exécutez simplement l’application, insérez-la directement dans le fichier *[AppName] .runtimeconfig.js* .</span><span class="sxs-lookup"><span data-stu-id="2c76d-124">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="2c76d-125">Le *.runtimeconfig.js[AppName] sur* le fichier sera remplacé lors des builds suivantes.</span><span class="sxs-lookup"><span data-stu-id="2c76d-125">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="2c76d-126">Spécifiez les options de configuration au moment de l’exécution dans la section **configProperties** du *runtimeconfig.jssur* les fichiers.</span><span class="sxs-lookup"><span data-stu-id="2c76d-126">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="2c76d-127">Cette section se présente sous la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="2c76d-127">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="2c76d-128">Exemple [AppName] .runtimeconfig.jssur le fichier</span><span class="sxs-lookup"><span data-stu-id="2c76d-128">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="2c76d-129">Si vous placez les options dans le fichier JSON de sortie, imbriquez-les sous la `runtimeOptions` propriété.</span><span class="sxs-lookup"><span data-stu-id="2c76d-129">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

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

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="2c76d-130">Exemple de runtimeconfig.template.jssur un fichier</span><span class="sxs-lookup"><span data-stu-id="2c76d-130">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="2c76d-131">Si vous placez les options dans le fichier JSON du modèle, omettez la `runtimeOptions` propriété.</span><span class="sxs-lookup"><span data-stu-id="2c76d-131">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="2c76d-132">MSBuild (propriétés)</span><span class="sxs-lookup"><span data-stu-id="2c76d-132">MSBuild properties</span></span>

<span data-ttu-id="2c76d-133">Certaines options de configuration au moment de l’exécution peuvent être définies à l’aide des propriétés MSBuild dans le fichier *. csproj* ou *. vbproj* des projets .net Core de type SDK.</span><span class="sxs-lookup"><span data-stu-id="2c76d-133">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="2c76d-134">Les propriétés MSBuild sont prioritaires sur les options définies dans le *runtimeconfig.template.jssur* le fichier.</span><span class="sxs-lookup"><span data-stu-id="2c76d-134">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="2c76d-135">Elles remplacent également toutes les options que vous définissez dans le *.runtimeconfig.js[AppName]* au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="2c76d-135">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="2c76d-136">Voici un exemple de fichier projet de type SDK avec des propriétés MSBuild pour la configuration du comportement au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="2c76d-136">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

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

<span data-ttu-id="2c76d-137">Les propriétés MSBuild pour la configuration du comportement au moment de l’exécution sont indiquées dans les articles individuels pour chaque zone, par exemple, [garbage collection](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="2c76d-137">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="2c76d-138">Ils sont également répertoriés dans la section Configuration de l' [exécution](../project-sdk/msbuild-props.md#run-time-configuration-properties) de la référence des propriétés MSBuild pour les projets de type SDK.</span><span class="sxs-lookup"><span data-stu-id="2c76d-138">They are also listed in the [Run-time configuration](../project-sdk/msbuild-props.md#run-time-configuration-properties) section of the MSBuild properties reference for SDK-style projects.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="2c76d-139">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="2c76d-139">Environment variables</span></span>

<span data-ttu-id="2c76d-140">Les variables d’environnement peuvent être utilisées pour fournir des informations de configuration au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2c76d-140">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="2c76d-141">La configuration d’une option au moment de l’exécution à l’aide d’une variable d’environnement applique le paramètre à toutes les applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2c76d-141">Configuring a run-time option by using an environment variable applies the setting to all .NET Core apps.</span></span> <span data-ttu-id="2c76d-142">Les boutons de configuration spécifiés en tant que variables d’environnement ont généralement le préfixe **COMPlus_**.</span><span class="sxs-lookup"><span data-stu-id="2c76d-142">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="2c76d-143">Vous pouvez définir des variables d’environnement à partir du panneau de configuration Windows, à partir de la ligne de commande ou par programme, en appelant la <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> méthode sur les systèmes Windows et UNIX.</span><span class="sxs-lookup"><span data-stu-id="2c76d-143">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="2c76d-144">Les exemples suivants montrent comment définir une variable d’environnement sur la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="2c76d-144">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
