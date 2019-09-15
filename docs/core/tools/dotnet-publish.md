---
title: Commande dotnet publish
description: La commande dotnet publish publie votre projet .NET Core dans un répertoire.
ms.date: 05/29/2018
ms.openlocfilehash: f9fea1a30e349ef949078e881756e2520d79ccbf
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969826"
---
# <a name="dotnet-publish"></a><span data-ttu-id="67646-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="67646-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="67646-104">Nom</span><span class="sxs-lookup"><span data-stu-id="67646-104">Name</span></span>

<span data-ttu-id="67646-105">`dotnet publish` - Empaquette l’application et ses dépendances dans un dossier en vue d’un déploiement sur un système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="67646-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="67646-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="67646-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="67646-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="67646-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="67646-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="67646-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="67646-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="67646-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="67646-110">Description</span><span class="sxs-lookup"><span data-stu-id="67646-110">Description</span></span>

<span data-ttu-id="67646-111">`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="67646-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="67646-112">La sortie inclut les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="67646-112">The output includes the following assets:</span></span>

- <span data-ttu-id="67646-113">Le code de langage intermédiaire (IL) dans un assembly avec l’extension *dll*.</span><span class="sxs-lookup"><span data-stu-id="67646-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="67646-114">Le fichier *.deps.json* qui inclut toutes les dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="67646-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="67646-115">Le fichier *.runtimeconfig.json* qui spécifie le runtime partagé attendu par l’application, ainsi que d’autres options de configuration pour le runtime (par exemple, le type de garbage collection).</span><span class="sxs-lookup"><span data-stu-id="67646-115">*.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="67646-116">Les dépendances de l’application, qui sont copiées à partir du cache NuGet dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="67646-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="67646-117">La sortie de la commande `dotnet publish` est prête pour le déploiement sur un système d’hébergement (par exemple, un serveur, PC, Mac, ordinateur portable) à des fins d’exécution.</span><span class="sxs-lookup"><span data-stu-id="67646-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="67646-118">Il s’agit de la seule façon officiellement prise en charge pour préparer l’application au déploiement.</span><span class="sxs-lookup"><span data-stu-id="67646-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="67646-119">En fonction du type de déploiement que spécifie le projet, le runtime .NET Core partagé peut ou non être installé sur le système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="67646-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="67646-120">Pour plus d’informations, consultez la page [Déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="67646-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="67646-121">Pour connaître la structure des répertoires d’une application publiée, consultez la page [Structure de répertoires](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="67646-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="67646-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="67646-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="67646-123">Projet à publier.</span><span class="sxs-lookup"><span data-stu-id="67646-123">The project to publish.</span></span> <span data-ttu-id="67646-124">Chemin et nom de fichier d’un fichier projet [C#](csproj.md), F# ou Visual Basic, ou chemin vers un répertoire qui contient un fichier projet C#, F# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="67646-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="67646-125">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="67646-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="67646-126">Options</span><span class="sxs-lookup"><span data-stu-id="67646-126">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="67646-127">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="67646-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="67646-128">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="67646-128">Defines the build configuration.</span></span> <span data-ttu-id="67646-129">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="67646-129">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="67646-130">Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="67646-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="67646-131">Le framework cible doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="67646-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="67646-132">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="67646-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="67646-133">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="67646-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="67646-134">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="67646-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="67646-135">Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application.</span><span class="sxs-lookup"><span data-stu-id="67646-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="67646-136">Le fichier manifeste fait partie de la sortie de la [commande `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="67646-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="67646-137">Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste.</span><span class="sxs-lookup"><span data-stu-id="67646-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="67646-138">Cette option est disponible à partir du SDK .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="67646-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="67646-139">Ne génère pas le projet avant la publication.</span><span class="sxs-lookup"><span data-stu-id="67646-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="67646-140">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="67646-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="67646-141">Ignore les références entre projets et restaure uniquement le projet racine.</span><span class="sxs-lookup"><span data-stu-id="67646-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="67646-142">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="67646-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="67646-143">Spécifie le chemin d’accès du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="67646-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="67646-144">Si aucune valeur n’est spécifiée, il s’agit par défaut de *./bin/[configuration]/[framework]/publish/* pour un déploiement dépendant du framework ou de *./bin/[configuration]/[framework]/[runtime]/publish/* pour un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="67646-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="67646-145">Si le chemin est relatif, le répertoire de sortie généré est relatif à l’emplacement du fichier projet, et non au répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="67646-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="67646-146">Publie le runtime .NET Core avec votre application ; ainsi, vous n’avez pas besoin d’installer le runtime sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="67646-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="67646-147">Si un identificateur de runtime est spécifié, sa valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="67646-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="67646-148">Pour plus d’informations sur les différents types de déploiement, consultez [Déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="67646-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="67646-149">Publie l’application pour un runtime donné.</span><span class="sxs-lookup"><span data-stu-id="67646-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="67646-150">Cette option est utilisée pour créer un [déploiement autonome (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="67646-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="67646-151">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="67646-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="67646-152">Par défaut, vous publiez un [déploiement dépendant du framework (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="67646-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="67646-153">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="67646-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="67646-154">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="67646-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="67646-155">Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="67646-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="67646-156">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="67646-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="67646-157">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="67646-157">Defines the build configuration.</span></span> <span data-ttu-id="67646-158">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="67646-158">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="67646-159">Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="67646-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="67646-160">Le framework cible doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="67646-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="67646-161">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="67646-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="67646-162">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="67646-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="67646-163">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="67646-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="67646-164">Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application.</span><span class="sxs-lookup"><span data-stu-id="67646-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="67646-165">Le fichier manifeste fait partie de la sortie de la [commande `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="67646-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="67646-166">Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste.</span><span class="sxs-lookup"><span data-stu-id="67646-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="67646-167">Cette option est disponible à partir du SDK .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="67646-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="67646-168">Ignore les références entre projets et restaure uniquement le projet racine.</span><span class="sxs-lookup"><span data-stu-id="67646-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="67646-169">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="67646-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="67646-170">Spécifie le chemin d’accès du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="67646-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="67646-171">Si aucune valeur n’est spécifiée, il s’agit par défaut de *./bin/[configuration]/[framework]/publish/* pour un déploiement dépendant du framework ou de *./bin/[configuration]/[framework]/[runtime]/publish/* pour un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="67646-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="67646-172">Si le chemin est relatif, le répertoire de sortie généré est relatif à l’emplacement du fichier projet, et non au répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="67646-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="67646-173">Publie le runtime .NET Core avec votre application ; ainsi, vous n’avez pas besoin d’installer le runtime sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="67646-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="67646-174">Si un identificateur de runtime est spécifié, sa valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="67646-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="67646-175">Pour plus d’informations sur les différents types de déploiement, consultez [Déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="67646-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="67646-176">Publie l’application pour un runtime donné.</span><span class="sxs-lookup"><span data-stu-id="67646-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="67646-177">Cette option est utilisée pour créer un [déploiement autonome (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="67646-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="67646-178">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="67646-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="67646-179">Par défaut, vous publiez un [déploiement dépendant du framework (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="67646-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="67646-180">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="67646-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="67646-181">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="67646-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="67646-182">Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="67646-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="67646-183">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="67646-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="67646-184">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="67646-184">Defines the build configuration.</span></span> <span data-ttu-id="67646-185">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="67646-185">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="67646-186">Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="67646-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="67646-187">Le framework cible doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="67646-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="67646-188">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="67646-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="67646-189">Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application.</span><span class="sxs-lookup"><span data-stu-id="67646-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="67646-190">Le fichier manifeste fait partie de la sortie de la [commande `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="67646-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="67646-191">Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste.</span><span class="sxs-lookup"><span data-stu-id="67646-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="67646-192">Cette option est disponible à partir du SDK .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="67646-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="67646-193">Spécifie le chemin d’accès du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="67646-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="67646-194">Si aucune valeur n’est spécifiée, il s’agit par défaut de *./bin/[configuration]/[framework]/publish/* pour un déploiement dépendant du framework ou de *./bin/[configuration]/[framework]/[runtime]/publish/* pour un déploiement autonome.</span><span class="sxs-lookup"><span data-stu-id="67646-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="67646-195">Si le chemin est relatif, le répertoire de sortie généré est relatif à l’emplacement du fichier projet, et non au répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="67646-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="67646-196">Publie l’application pour un runtime donné.</span><span class="sxs-lookup"><span data-stu-id="67646-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="67646-197">Cette option est utilisée pour créer un [déploiement autonome (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="67646-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="67646-198">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="67646-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="67646-199">Par défaut, vous publiez un [déploiement dépendant du framework (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="67646-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="67646-200">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="67646-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="67646-201">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="67646-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="67646-202">Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="67646-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="67646-203">Exemples</span><span class="sxs-lookup"><span data-stu-id="67646-203">Examples</span></span>

<span data-ttu-id="67646-204">Publier le projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="67646-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="67646-205">Publier l’application à l’aide du fichier projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="67646-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="67646-206">Publier le projet dans le répertoire actif à l’aide du framework `netcoreapp1.1` :</span><span class="sxs-lookup"><span data-stu-id="67646-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="67646-207">Publier l’application actuelle à l’aide du framework `netcoreapp1.1` et du runtime pour `OS X 10.10` (vous devez lister cet identificateur de runtime dans le fichier projet) :</span><span class="sxs-lookup"><span data-stu-id="67646-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="67646-208">Publier l’application actuelle, mais ne pas restaurer les références de projet à projet (P2P), seulement le projet racine durant l’opération de restauration (SDK .NET Core 2.0 et ultérieur) :</span><span class="sxs-lookup"><span data-stu-id="67646-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="67646-209">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67646-209">See also</span></span>

- [<span data-ttu-id="67646-210">Frameworks cibles</span><span class="sxs-lookup"><span data-stu-id="67646-210">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="67646-211">Catalogue d’identificateurs de runtime (RID)</span><span class="sxs-lookup"><span data-stu-id="67646-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
