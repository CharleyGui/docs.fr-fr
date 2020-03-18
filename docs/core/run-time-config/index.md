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
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="d34b2-103">paramètres de configuration de temps d’exécution .NET Core</span><span class="sxs-lookup"><span data-stu-id="d34b2-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="d34b2-104">.NET Core prend en charge l’utilisation de fichiers de configuration et de variables de l’environnement pour configurer le comportement des applications .NET Core au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d34b2-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="d34b2-105">La configuration du temps d’exécution est une option intéressante si :</span><span class="sxs-lookup"><span data-stu-id="d34b2-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="d34b2-106">Vous ne possédez pas ou ne contrôlez pas le code source d’une application et vous ne pouvez donc pas le configurer de manière programmatique.</span><span class="sxs-lookup"><span data-stu-id="d34b2-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="d34b2-107">Plusieurs instances de votre application s’exécutent en même temps sur un seul système, et vous souhaitez configurer chacune pour des performances optimales.</span><span class="sxs-lookup"><span data-stu-id="d34b2-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="d34b2-108">Cette documentation est un travail en cours.</span><span class="sxs-lookup"><span data-stu-id="d34b2-108">This documentation is a work in progress.</span></span> <span data-ttu-id="d34b2-109">Si vous remarquez que les renseignements présentés ici sont incomplets ou inexacts, soit [ouvrez une question](https://github.com/dotnet/docs/issues) pour nous le faire savoir, soit [soumettez une demande de retrait](https://github.com/dotnet/docs/pulls) pour régler le problème.</span><span class="sxs-lookup"><span data-stu-id="d34b2-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="d34b2-110">Pour obtenir de [l’information](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md)sur la soumission de demandes de retrait pour le référentiel dotnet/docs, consultez le guide du contributeur .</span><span class="sxs-lookup"><span data-stu-id="d34b2-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="d34b2-111">.NET Core fournit les mécanismes suivants pour configurer le comportement d’application en temps d’exécution :</span><span class="sxs-lookup"><span data-stu-id="d34b2-111">.NET Core provides the following mechanisms for configuring run-time application behavior:</span></span>

- <span data-ttu-id="d34b2-112">Le [fichier runtimeconfig.json](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="d34b2-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="d34b2-113">Propriétés MSBuild</span><span class="sxs-lookup"><span data-stu-id="d34b2-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="d34b2-114">Variables de l’environnement</span><span class="sxs-lookup"><span data-stu-id="d34b2-114">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="d34b2-115">Certaines valeurs de configuration peuvent également être <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> définies programmatiquement en appelant la méthode.</span><span class="sxs-lookup"><span data-stu-id="d34b2-115">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="d34b2-116">Les articles de cette section de la documentation sont organisés par catégorie, par exemple, [le débogage](debugging-profiling.md) et [la collecte des ordures](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="d34b2-116">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="d34b2-117">Le cas échéant, les options de configuration sont affichées pour les fichiers *runtimeconfig.json,* les propriétés MSBuild, les variables de l’environnement et, pour les fichiers *app.config* de référence croisées pour les projets cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="d34b2-117">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="d34b2-118">runtimeconfig.json</span><span class="sxs-lookup"><span data-stu-id="d34b2-118">runtimeconfig.json</span></span>

<span data-ttu-id="d34b2-119">Lorsqu’un projet est [construit,](../tools/dotnet-build.md)un fichier *[appname].runtimeconfig.json* est généré dans l’annuaire de sortie.</span><span class="sxs-lookup"><span data-stu-id="d34b2-119">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="d34b2-120">Si un fichier *runtimeconfig.template.json* existe dans le même dossier que le fichier de projet, toutes les options de configuration qu’il contient sont fusionnées dans le fichier *[appname].runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="d34b2-120">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="d34b2-121">Si vous construisez l’application vous-même, placez toutes les options de configuration dans le fichier *runtimeconfig.template.json.*</span><span class="sxs-lookup"><span data-stu-id="d34b2-121">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="d34b2-122">Si vous êtes juste en cours d’exécution de l’application, les insérer directement dans le *fichier [appname].runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="d34b2-122">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="d34b2-123">Le *fichier [appname].runtimeconfig.json* sera écrasé sur les builds suivants.</span><span class="sxs-lookup"><span data-stu-id="d34b2-123">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="d34b2-124">Spécifier les options de configuration en temps d’exécution dans la section **configProperties** des fichiers *runtimeconfig.json.*</span><span class="sxs-lookup"><span data-stu-id="d34b2-124">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="d34b2-125">Cette section a le formulaire:</span><span class="sxs-lookup"><span data-stu-id="d34b2-125">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="d34b2-126">Exemple [appname].runtimeconfig.json fichier</span><span class="sxs-lookup"><span data-stu-id="d34b2-126">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="d34b2-127">Si vous placez les options dans le fichier de `runtimeOptions` sortie JSON, entrez-les sous la propriété.</span><span class="sxs-lookup"><span data-stu-id="d34b2-127">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

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

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="d34b2-128">Exemple de fichier runtimeconfig.template.json</span><span class="sxs-lookup"><span data-stu-id="d34b2-128">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="d34b2-129">Si vous placez les options dans le fichier `runtimeOptions` JSON modèle, omettre la propriété.</span><span class="sxs-lookup"><span data-stu-id="d34b2-129">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="d34b2-130">MSBuild (propriétés)</span><span class="sxs-lookup"><span data-stu-id="d34b2-130">MSBuild properties</span></span>

<span data-ttu-id="d34b2-131">Certaines options de configuration en temps d’exécution peuvent être définies à l’aide de propriétés MSBuild dans le fichier *.csproj* ou *.vbproj* des projets .NET Core de style SDK.</span><span class="sxs-lookup"><span data-stu-id="d34b2-131">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="d34b2-132">Les propriétés MSBuild ont préséance sur les options définies dans le fichier *runtimeconfig.template.json.*</span><span class="sxs-lookup"><span data-stu-id="d34b2-132">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="d34b2-133">Ils surcrivent également toutes les options que vous définissez dans le *fichier [appname].runtimeconfig.json* au moment de la construction.</span><span class="sxs-lookup"><span data-stu-id="d34b2-133">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="d34b2-134">Voici un exemple de fichier de projet de type SDK avec des propriétés MSBuild pour configurer le comportement en temps de course :</span><span class="sxs-lookup"><span data-stu-id="d34b2-134">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

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

<span data-ttu-id="d34b2-135">MsBuild propriétés pour configurer le comportement de temps de course sont notés dans les articles individuels pour chaque zone, par exemple, [la collecte des ordures](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="d34b2-135">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span>

## <a name="environment-variables"></a><span data-ttu-id="d34b2-136">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="d34b2-136">Environment variables</span></span>

<span data-ttu-id="d34b2-137">Les variables de l’environnement peuvent être utilisées pour fournir des informations de configuration en temps de course.</span><span class="sxs-lookup"><span data-stu-id="d34b2-137">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="d34b2-138">Les boutons de configuration spécifiés comme variables d’environnement ont généralement le préfixe **COMPlus_**.</span><span class="sxs-lookup"><span data-stu-id="d34b2-138">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="d34b2-139">Vous pouvez définir les variables de l’environnement à partir du panneau <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> de contrôle Windows, à la ligne de commande, ou de manière programmatique en appelant la méthode sur les systèmes Windows et Unix.</span><span class="sxs-lookup"><span data-stu-id="d34b2-139">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="d34b2-140">Les exemples suivants montrent comment définir une variable d’environnement à la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="d34b2-140">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
