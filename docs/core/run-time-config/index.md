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
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="45802-103">Paramètres de configuration du Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="45802-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="45802-104">.NET Core prend en charge l’utilisation de fichiers de configuration et de variables d’environnement pour configurer le comportement des applications .NET Core au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="45802-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="45802-105">La configuration au moment de l’exécution est une option attrayante dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="45802-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="45802-106">Vous ne possédez pas ou ne contrôlez pas le code source d’une application. par conséquent, vous ne pouvez pas le configurer par programme.</span><span class="sxs-lookup"><span data-stu-id="45802-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="45802-107">Plusieurs instances de votre application s’exécutent en même temps sur un système unique et vous souhaitez configurer chacune d’elles pour obtenir des performances optimales.</span><span class="sxs-lookup"><span data-stu-id="45802-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="45802-108">Cette documentation est un travail en cours.</span><span class="sxs-lookup"><span data-stu-id="45802-108">This documentation is a work in progress.</span></span> <span data-ttu-id="45802-109">Si vous remarquez que les informations présentées ici sont incomplètes ou inexactes, vous pouvez soit [ouvrir un problème](https://github.com/dotnet/docs/issues) pour nous le faire savoir, soit [soumettre une demande de tirage](https://github.com/dotnet/docs/pulls) pour résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="45802-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="45802-110">Pour plus d’informations sur l’envoi de requêtes de tirage pour le dépôt dotnet/docs, consultez le [Guide du contributeur](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="45802-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="45802-111">.NET Core fournit les mécanismes suivants pour configurer le comportement de l’application au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="45802-111">.NET Core provides the following mechanisms for configuring run-time application behavior:</span></span>

- <span data-ttu-id="45802-112">Le [fichier runtimeconfig. JSON](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="45802-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="45802-113">Propriétés MSBuild</span><span class="sxs-lookup"><span data-stu-id="45802-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="45802-114">Variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="45802-114">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="45802-115">Certaines valeurs de configuration peuvent également être définies par programmation en appelant la méthode <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="45802-115">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="45802-116">Les Articles de cette section de la documentation sont organisés par catégorie, par exemple, [débogage](debugging-profiling.md) et [garbage collection](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="45802-116">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="45802-117">Le cas échéant, des options de configuration s’affichent pour les fichiers *runtimeconfig. JSON* , les propriétés MSBuild, les variables d’environnement et, pour les références croisées, les fichiers *app. config* pour les projets .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45802-117">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="45802-118">runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="45802-118">runtimeconfig.json</span></span>

<span data-ttu-id="45802-119">Lorsqu’un projet est [généré](../tools/dotnet-build.md), un fichier *[AppName]. runtimeconfig. JSON* est généré dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="45802-119">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="45802-120">Si un fichier *runtimeconfig. template. JSON* se trouve dans le même dossier que le fichier projet, toutes les options de configuration qu’il contient sont fusionnées dans le fichier *[AppName]. runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="45802-120">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="45802-121">Si vous créez l’application vous-même, placez toutes les options de configuration dans le fichier *runtimeconfig. template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="45802-121">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="45802-122">Si vous exécutez simplement l’application, insérez-la directement dans le fichier *[AppName]. runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="45802-122">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="45802-123">Le fichier *[AppName]. runtimeconfig. JSON* sera remplacé lors des builds suivantes.</span><span class="sxs-lookup"><span data-stu-id="45802-123">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="45802-124">Spécifiez les options de configuration au moment de l’exécution dans la section **configProperties** des fichiers *runtimeconfig. JSON* .</span><span class="sxs-lookup"><span data-stu-id="45802-124">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="45802-125">Cette section se présente sous la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="45802-125">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="45802-126">Exemple de fichier [AppName]. runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="45802-126">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="45802-127">Si vous placez les options dans le fichier JSON de sortie, imbriquez-les sous la propriété `runtimeOptions`.</span><span class="sxs-lookup"><span data-stu-id="45802-127">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

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

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="45802-128">Exemple de fichier runtimeconfig. template. JSON</span><span class="sxs-lookup"><span data-stu-id="45802-128">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="45802-129">Si vous placez les options dans le fichier JSON du modèle, omettez la propriété `runtimeOptions`.</span><span class="sxs-lookup"><span data-stu-id="45802-129">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="45802-130">MSBuild (propriétés)</span><span class="sxs-lookup"><span data-stu-id="45802-130">MSBuild properties</span></span>

<span data-ttu-id="45802-131">Certaines options de configuration au moment de l’exécution peuvent être définies à l’aide des propriétés MSBuild dans le fichier *. csproj* ou *. vbproj* des projets .net Core de type SDK.</span><span class="sxs-lookup"><span data-stu-id="45802-131">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="45802-132">Les propriétés MSBuild sont prioritaires sur les options définies dans le fichier *runtimeconfig. template. JSON* .</span><span class="sxs-lookup"><span data-stu-id="45802-132">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="45802-133">Elles remplacent également toutes les options que vous définissez dans le fichier *[AppName]. runtimeconfig. JSON* au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="45802-133">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="45802-134">Voici un exemple de fichier projet de type SDK avec des propriétés MSBuild pour la configuration du comportement au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="45802-134">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

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

<span data-ttu-id="45802-135">Les propriétés MSBuild pour la configuration du comportement au moment de l’exécution sont indiquées dans les articles individuels pour chaque zone, par exemple, [garbage collection](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="45802-135">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span>

## <a name="environment-variables"></a><span data-ttu-id="45802-136">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="45802-136">Environment variables</span></span>

<span data-ttu-id="45802-137">Les variables d’environnement peuvent être utilisées pour fournir des informations de configuration au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="45802-137">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="45802-138">Les boutons de configuration spécifiés en tant que variables d’environnement ont généralement le préfixe **COMPlus_** .</span><span class="sxs-lookup"><span data-stu-id="45802-138">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="45802-139">Vous pouvez définir des variables d’environnement à partir du panneau de configuration Windows, à partir de la ligne de commande ou par programme, en appelant la méthode <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> sur les systèmes Windows et UNIX.</span><span class="sxs-lookup"><span data-stu-id="45802-139">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="45802-140">Les exemples suivants montrent comment définir une variable d’environnement sur la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="45802-140">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
