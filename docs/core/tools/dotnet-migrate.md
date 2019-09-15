---
title: Commande dotnet migrate
description: La commande dotnet migrate permet de migrer un projet et l’ensemble de ses dépendances.
ms.date: 08/08/2019
ms.openlocfilehash: 790c607070ff348ca7cfe30137268de18dcb0293
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990428"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="76eba-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="76eba-103">dotnet migrate</span></span>

<span data-ttu-id="76eba-104">**Cet article s’applique à : ✓** .net Core 1. x SDK **✓** .net Core 2. x SDK</span><span class="sxs-lookup"><span data-stu-id="76eba-104">**This article applies to: ✓** .NET Core 1.x SDK **✓** .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="76eba-105">Name</span><span class="sxs-lookup"><span data-stu-id="76eba-105">Name</span></span>

<span data-ttu-id="76eba-106">`dotnet migrate` : migre un projet .NET Core Preview 2 vers un projet de style SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="76eba-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="76eba-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="76eba-107">Synopsis</span></span>

```console
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="76eba-108">Description</span><span class="sxs-lookup"><span data-stu-id="76eba-108">Description</span></span>

<span data-ttu-id="76eba-109">La commande `dotnet migrate` migre un projet *project.json* Preview 2 valide vers un projet *csproj* de style SDK .NET Core valide.</span><span class="sxs-lookup"><span data-stu-id="76eba-109">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK-style *csproj* project.</span></span>

<span data-ttu-id="76eba-110">Par défaut, la commande migre le projet racine et toutes les références de projet qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="76eba-110">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="76eba-111">Ce comportement peut être désactivé à l’aide de l’option `--skip-project-references` au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="76eba-111">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="76eba-112">La migration peut être effectuée sur les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="76eba-112">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="76eba-113">Un projet unique en spécifiant le fichier *project.json* à migrer.</span><span class="sxs-lookup"><span data-stu-id="76eba-113">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="76eba-114">Tous les répertoires spécifiés dans le fichier *global.json* en passant un chemin du fichier *global.json*.</span><span class="sxs-lookup"><span data-stu-id="76eba-114">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="76eba-115">Un fichier *solution.sln*, où il migre les projets référencés dans la solution.</span><span class="sxs-lookup"><span data-stu-id="76eba-115">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="76eba-116">Sur tous les sous-répertoires du répertoire donné de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="76eba-116">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="76eba-117">La commande `dotnet migrate` conserve le fichier *project.json* migré dans un répertoire `backup`, qu’elle crée s’il n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="76eba-117">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="76eba-118">Ce comportement est remplacé à l’aide de l’option `--skip-backup`.</span><span class="sxs-lookup"><span data-stu-id="76eba-118">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="76eba-119">Par défaut, l’opération de migration affiche l’état du processus de migration dans la sortie standard (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="76eba-119">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="76eba-120">Si vous utilisez l’option `--report-file <REPORT_FILE>`, la sortie est enregistrée dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="76eba-120">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="76eba-121">La commande `dotnet migrate` prend en charge uniquement les projets *project.json* Preview 2 valides.</span><span class="sxs-lookup"><span data-stu-id="76eba-121">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="76eba-122">Cela signifie que vous ne pouvez pas l’utiliser pour migrer des projets *project.json* DNX ou Preview 1 directement vers des projets MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="76eba-122">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="76eba-123">Vous devez tout d’abord migrer manuellement le projet vers un projet *project.json* Preview 2, puis utiliser la commande `dotnet migrate` pour migrer le projet.</span><span class="sxs-lookup"><span data-stu-id="76eba-123">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

<span data-ttu-id="76eba-124">La `dotnet migrate` commande n’est plus disponible à partir du kit de développement logiciel (SDK) .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="76eba-124">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span>

## <a name="arguments"></a><span data-ttu-id="76eba-125">Arguments</span><span class="sxs-lookup"><span data-stu-id="76eba-125">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="76eba-126">Le chemin d’accès à l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="76eba-126">The path to one of the following:</span></span>

* <span data-ttu-id="76eba-127">Un fichier *project.json* à migrer.</span><span class="sxs-lookup"><span data-stu-id="76eba-127">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="76eba-128">Un fichier *global.json* : les dossiers spécifiés dans *global.json* sont migrés.</span><span class="sxs-lookup"><span data-stu-id="76eba-128">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="76eba-129">Un fichier *solution.sln* : les projets référencés dans la solution sont migrés.</span><span class="sxs-lookup"><span data-stu-id="76eba-129">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="76eba-130">Un répertoire à migrer : recherche de manière récursive des fichiers *project.json* à migrer à l’intérieur du répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="76eba-130">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="76eba-131">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="76eba-131">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="76eba-132">Options</span><span class="sxs-lookup"><span data-stu-id="76eba-132">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="76eba-133">Génère le fichier de rapport de migration au format JSON plutôt que sous la forme de messages utilisateur.</span><span class="sxs-lookup"><span data-stu-id="76eba-133">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="76eba-134">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="76eba-134">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="76eba-135">Génère un rapport de migration dans un fichier, en plus de le faire dans la console.</span><span class="sxs-lookup"><span data-stu-id="76eba-135">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="76eba-136">Ignore la migration des références de projet.</span><span class="sxs-lookup"><span data-stu-id="76eba-136">Skip migrating project references.</span></span> <span data-ttu-id="76eba-137">Par défaut, les références de projet sont migrées de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="76eba-137">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="76eba-138">Ignore le déplacement de *project.json*, *global.json* et *\*.xproj* vers un répertoire `backup` après la migration.</span><span class="sxs-lookup"><span data-stu-id="76eba-138">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="76eba-139">Fichier csproj de modèle à utiliser pour la migration.</span><span class="sxs-lookup"><span data-stu-id="76eba-139">Template csproj file to use for migration.</span></span> <span data-ttu-id="76eba-140">Par défaut, le même modèle que celui déposé par `dotnet new console` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="76eba-140">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="76eba-141">Version du package de SDK à référencer dans l’application migrée.</span><span class="sxs-lookup"><span data-stu-id="76eba-141">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="76eba-142">La valeur par défaut est la version du SDK dans `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="76eba-142">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="76eba-143">Chemin du fichier xproj à utiliser.</span><span class="sxs-lookup"><span data-stu-id="76eba-143">The path to the xproj file to use.</span></span> <span data-ttu-id="76eba-144">Requis quand il existe plusieurs xproj dans un répertoire de projet.</span><span class="sxs-lookup"><span data-stu-id="76eba-144">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="76eba-145">Exemples</span><span class="sxs-lookup"><span data-stu-id="76eba-145">Examples</span></span>

<span data-ttu-id="76eba-146">Migrer un projet et toutes ses dépendances de projet à projet vers le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="76eba-146">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="76eba-147">Migrer tous les projets que le fichier *global.json* contient :</span><span class="sxs-lookup"><span data-stu-id="76eba-147">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="76eba-148">Migrer uniquement le projet actuel et aucune dépendance de projet à projet (P2P).</span><span class="sxs-lookup"><span data-stu-id="76eba-148">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="76eba-149">En outre, utilisez une version de Kit de développement logiciel (SDK) spécifique :</span><span class="sxs-lookup"><span data-stu-id="76eba-149">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
