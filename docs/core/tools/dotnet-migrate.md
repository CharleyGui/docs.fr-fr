---
title: Commande dotnet migrate
description: La commande dotnet migrate permet de migrer un projet et l’ensemble de ses dépendances.
ms.date: 06/26/2019
ms.openlocfilehash: 86f11592e774da12b010886aaa1e30cee063fea6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202534"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="f6833-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="f6833-103">dotnet migrate</span></span>

<span data-ttu-id="f6833-104">**Cette rubrique s’applique à : ✓** SDK .NET Core 1.x et ultérieur</span><span class="sxs-lookup"><span data-stu-id="f6833-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="f6833-105">Name</span><span class="sxs-lookup"><span data-stu-id="f6833-105">Name</span></span>

<span data-ttu-id="f6833-106">`dotnet migrate` : migre un projet .NET Core Preview 2 vers un projet de style SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f6833-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

> [!NOTE]
> <span data-ttu-id="f6833-107">`dotnet migrate` sera retiré du SDK .NET Core 3.0 dans la prochaine préversion.</span><span class="sxs-lookup"><span data-stu-id="f6833-107">`dotnet migrate` will be removed from the .NET Core 3.0 SDK in the next preview release.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f6833-108">Résumé</span><span class="sxs-lookup"><span data-stu-id="f6833-108">Synopsis</span></span>

```console
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f6833-109">Description</span><span class="sxs-lookup"><span data-stu-id="f6833-109">Description</span></span>

<span data-ttu-id="f6833-110">La commande `dotnet migrate` migre un projet *project.json* Preview 2 valide vers un projet *csproj* de style SDK .NET Core valide.</span><span class="sxs-lookup"><span data-stu-id="f6833-110">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK-style *csproj* project.</span></span>

<span data-ttu-id="f6833-111">Par défaut, la commande migre le projet racine et toutes les références de projet qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="f6833-111">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="f6833-112">Ce comportement peut être désactivé à l’aide de l’option `--skip-project-references` au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f6833-112">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="f6833-113">La migration peut être effectuée sur les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="f6833-113">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="f6833-114">Un projet unique en spécifiant le fichier *project.json* à migrer.</span><span class="sxs-lookup"><span data-stu-id="f6833-114">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="f6833-115">Tous les répertoires spécifiés dans le fichier *global.json* en passant un chemin du fichier *global.json*.</span><span class="sxs-lookup"><span data-stu-id="f6833-115">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="f6833-116">Un fichier *solution.sln*, où il migre les projets référencés dans la solution.</span><span class="sxs-lookup"><span data-stu-id="f6833-116">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="f6833-117">Sur tous les sous-répertoires du répertoire donné de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="f6833-117">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="f6833-118">La commande `dotnet migrate` conserve le fichier *project.json* migré dans un répertoire `backup`, qu’elle crée s’il n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="f6833-118">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="f6833-119">Ce comportement est remplacé à l’aide de l’option `--skip-backup`.</span><span class="sxs-lookup"><span data-stu-id="f6833-119">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="f6833-120">Par défaut, l’opération de migration affiche l’état du processus de migration dans la sortie standard (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="f6833-120">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="f6833-121">Si vous utilisez l’option `--report-file <REPORT_FILE>`, la sortie est enregistrée dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="f6833-121">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="f6833-122">La commande `dotnet migrate` prend en charge uniquement les projets *project.json* Preview 2 valides.</span><span class="sxs-lookup"><span data-stu-id="f6833-122">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="f6833-123">Cela signifie que vous ne pouvez pas l’utiliser pour migrer des projets *project.json* DNX ou Preview 1 directement vers des projets MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="f6833-123">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="f6833-124">Vous devez tout d’abord migrer manuellement le projet vers un projet *project.json* Preview 2, puis utiliser la commande `dotnet migrate` pour migrer le projet.</span><span class="sxs-lookup"><span data-stu-id="f6833-124">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="f6833-125">Arguments</span><span class="sxs-lookup"><span data-stu-id="f6833-125">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="f6833-126">Le chemin d’accès à l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f6833-126">The path to one of the following:</span></span>

* <span data-ttu-id="f6833-127">Un fichier *project.json* à migrer.</span><span class="sxs-lookup"><span data-stu-id="f6833-127">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="f6833-128">Un fichier *global.json* : les dossiers spécifiés dans *global.json* sont migrés.</span><span class="sxs-lookup"><span data-stu-id="f6833-128">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="f6833-129">Un fichier *solution.sln* : les projets référencés dans la solution sont migrés.</span><span class="sxs-lookup"><span data-stu-id="f6833-129">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="f6833-130">Un répertoire à migrer : recherche de manière récursive des fichiers *project.json* à migrer à l’intérieur du répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="f6833-130">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="f6833-131">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="f6833-131">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="f6833-132">Options</span><span class="sxs-lookup"><span data-stu-id="f6833-132">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="f6833-133">Génère le fichier de rapport de migration au format JSON plutôt que sous la forme de messages utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f6833-133">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="f6833-134">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="f6833-134">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="f6833-135">Génère un rapport de migration dans un fichier, en plus de le faire dans la console.</span><span class="sxs-lookup"><span data-stu-id="f6833-135">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="f6833-136">Ignore la migration des références de projet.</span><span class="sxs-lookup"><span data-stu-id="f6833-136">Skip migrating project references.</span></span> <span data-ttu-id="f6833-137">Par défaut, les références de projet sont migrées de manière récursive.</span><span class="sxs-lookup"><span data-stu-id="f6833-137">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="f6833-138">Ignore le déplacement de *project.json*, *global.json* et *\*.xproj* vers un répertoire `backup` après la migration.</span><span class="sxs-lookup"><span data-stu-id="f6833-138">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="f6833-139">Fichier csproj de modèle à utiliser pour la migration.</span><span class="sxs-lookup"><span data-stu-id="f6833-139">Template csproj file to use for migration.</span></span> <span data-ttu-id="f6833-140">Par défaut, le même modèle que celui déposé par `dotnet new console` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f6833-140">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="f6833-141">Version du package de SDK à référencer dans l’application migrée.</span><span class="sxs-lookup"><span data-stu-id="f6833-141">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="f6833-142">La valeur par défaut est la version du SDK dans `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="f6833-142">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="f6833-143">Chemin du fichier xproj à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f6833-143">The path to the xproj file to use.</span></span> <span data-ttu-id="f6833-144">Requis quand il existe plusieurs xproj dans un répertoire de projet.</span><span class="sxs-lookup"><span data-stu-id="f6833-144">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="f6833-145">Exemples</span><span class="sxs-lookup"><span data-stu-id="f6833-145">Examples</span></span>

<span data-ttu-id="f6833-146">Migrer un projet et toutes ses dépendances de projet à projet vers le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="f6833-146">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="f6833-147">Migrer tous les projets que le fichier *global.json* contient :</span><span class="sxs-lookup"><span data-stu-id="f6833-147">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="f6833-148">Migrer uniquement le projet actuel et aucune dépendance de projet à projet (P2P).</span><span class="sxs-lookup"><span data-stu-id="f6833-148">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="f6833-149">En outre, utilisez une version de Kit de développement logiciel (SDK) spécifique :</span><span class="sxs-lookup"><span data-stu-id="f6833-149">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
