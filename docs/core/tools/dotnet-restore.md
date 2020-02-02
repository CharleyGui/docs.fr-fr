---
title: Commande dotnet restore
description: Découvrez comment restaurer les dépendances et les outils spécifiques du projet avec la commande dotnet restore.
ms.date: 05/29/2018
ms.openlocfilehash: dc73b7b2482d25872be922e68103fb86067146f7
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920562"
---
# <a name="dotnet-restore"></a><span data-ttu-id="43c8c-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="43c8c-103">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="43c8c-104">Name</span><span class="sxs-lookup"><span data-stu-id="43c8c-104">Name</span></span>

<span data-ttu-id="43c8c-105">`dotnet restore` : Restaure les dépendances et les outils d’un projet.</span><span class="sxs-lookup"><span data-stu-id="43c8c-105">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="43c8c-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="43c8c-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="43c8c-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="43c8c-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="43c8c-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="43c8c-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="43c8c-109">Description</span><span class="sxs-lookup"><span data-stu-id="43c8c-109">Description</span></span>

<span data-ttu-id="43c8c-110">La commande `dotnet restore` utilise NuGet pour restaurer les dépendances, ainsi que les outils spécifiques aux projets qui sont spécifiés dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="43c8c-110">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="43c8c-111">Par défaut, la restauration des dépendances et celle des outils sont exécutées en parallèle.</span><span class="sxs-lookup"><span data-stu-id="43c8c-111">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="43c8c-112">Pour restaurer les dépendances, NuGet a besoin des flux où sont situés les packages.</span><span class="sxs-lookup"><span data-stu-id="43c8c-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="43c8c-113">Les flux sont généralement fournis via le fichier de configuration *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="43c8c-113">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="43c8c-114">Un fichier de configuration par défaut est fourni lors de l’installation du kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="43c8c-114">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="43c8c-115">Vous pouvez spécifier d’autres flux en créant votre propre fichier *nuget.config* dans le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="43c8c-115">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="43c8c-116">Vous pouvez remplacer les flux *NuGet. config* par l’option `-s`.</span><span class="sxs-lookup"><span data-stu-id="43c8c-116">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="43c8c-117">Pour les dépendances, vous pouvez spécifier l’emplacement des packages restaurés pendant l’opération de restauration à l’aide de l’argument `--packages`.</span><span class="sxs-lookup"><span data-stu-id="43c8c-117">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="43c8c-118">Si aucune valeur n’est spécifiée, le cache du package NuGet par défaut est utilisé. Il se trouve dans le répertoire `.nuget/packages`, situé dans le répertoire de base de l’utilisateur, sur tous les systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="43c8c-118">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="43c8c-119">Par exemple, */home/user1* sur Linux ou *C:\Users\user1* sur Windows.</span><span class="sxs-lookup"><span data-stu-id="43c8c-119">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="43c8c-120">Pour les outils spécifiques au projet, `dotnet restore` commence par restaurer le package dans lequel l’outil est empaqueté, puis il restaure les dépendances de l’outil, comme spécifié dans son fichier projet.</span><span class="sxs-lookup"><span data-stu-id="43c8c-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="43c8c-121">Différences dans nuget.config</span><span class="sxs-lookup"><span data-stu-id="43c8c-121">nuget.config differences</span></span>

<span data-ttu-id="43c8c-122">Le comportement de la commande `dotnet restore` est affecté par les paramètres du fichier *nuget.config*, s’il est présent.</span><span class="sxs-lookup"><span data-stu-id="43c8c-122">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="43c8c-123">Par exemple, si vous définissez `globalPackagesFolder` dans *nuget.config*, les packages NuGet restaurés sont placés dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="43c8c-123">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="43c8c-124">Cette méthode permet également de spécifier l’option `--packages` sur la commande `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="43c8c-124">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="43c8c-125">Pour plus d’informations, consultez [Informations de référence sur nuget.config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="43c8c-125">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="43c8c-126">Trois paramètres spécifiques sont ignorés par `dotnet restore` :</span><span class="sxs-lookup"><span data-stu-id="43c8c-126">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="43c8c-127">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="43c8c-127">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="43c8c-128">Les redirections de liaison ne fonctionnent pas avec les éléments `<PackageReference>` et .NET Core prend en charge seulement les éléments `<PackageReference>` pour les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="43c8c-128">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="43c8c-129">solution</span><span class="sxs-lookup"><span data-stu-id="43c8c-129">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="43c8c-130">Ce paramètre est spécifique à Visual Studio et ne s’applique pas à .NET Core.</span><span class="sxs-lookup"><span data-stu-id="43c8c-130">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="43c8c-131">.NET Core n’utilise pas de fichier `packages.config` et utilise à la place des éléments `<PackageReference>` pour les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="43c8c-131">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="43c8c-132">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="43c8c-132">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="43c8c-133">Ce paramètre n’est pas applicable, car [NuGet ne prend pas encore en charge la vérification multiplateforme](https://github.com/NuGet/Home/issues/7939) des packages approuvés.</span><span class="sxs-lookup"><span data-stu-id="43c8c-133">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="43c8c-134">`dotnet restore` implicite</span><span class="sxs-lookup"><span data-stu-id="43c8c-134">Implicit `dotnet restore`</span></span>

<span data-ttu-id="43c8c-135">À compter de .NET Core 2.0, `dotnet restore` est au besoin exécuté implicitement quand vous exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="43c8c-135">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="43c8c-136">Dans la plupart des cas, vous n’avez plus besoin d’utiliser explicitement la commande `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="43c8c-136">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="43c8c-137">Parfois, il peut s’avérer fastidieux d’exécuter `dotnet restore` implicitement.</span><span class="sxs-lookup"><span data-stu-id="43c8c-137">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="43c8c-138">Par exemple, certains systèmes automatisés, comme les systèmes de génération, doivent appeler explicitement `dotnet restore` pour contrôler quand la restauration a lieu afin de pouvoir contrôler l’utilisation du réseau.</span><span class="sxs-lookup"><span data-stu-id="43c8c-138">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="43c8c-139">Pour empêcher l’exécution implicite de `dotnet restore`, vous pouvez utiliser l’indicateur `--no-restore` avec l’une de ces commandes afin de désactiver la restauration implicite.</span><span class="sxs-lookup"><span data-stu-id="43c8c-139">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="43c8c-140">Arguments</span><span class="sxs-lookup"><span data-stu-id="43c8c-140">Arguments</span></span>

`ROOT`

<span data-ttu-id="43c8c-141">Chemin facultatif du fichier projet à restaurer.</span><span class="sxs-lookup"><span data-stu-id="43c8c-141">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="43c8c-142">Options</span><span class="sxs-lookup"><span data-stu-id="43c8c-142">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="43c8c-143">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="43c8c-143">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="43c8c-144">Fichier de configuration NuGet (*nuget.config*) à utiliser pour l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="43c8c-144">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="43c8c-145">Désactive la restauration de plusieurs projets en parallèle.</span><span class="sxs-lookup"><span data-stu-id="43c8c-145">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="43c8c-146">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="43c8c-146">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="43c8c-147">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="43c8c-147">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="43c8c-148">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="43c8c-148">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="43c8c-149">N’avertit en cas d’échec des sources que si des packages répondent aux exigences de versions.</span><span class="sxs-lookup"><span data-stu-id="43c8c-149">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="43c8c-150">Spécifie de ne pas mettre en cache les packages et les requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="43c8c-150">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="43c8c-151">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="43c8c-151">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="43c8c-152">Spécifie le répertoire des packages restaurés.</span><span class="sxs-lookup"><span data-stu-id="43c8c-152">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="43c8c-153">Spécifie un runtime pour la restauration du package.</span><span class="sxs-lookup"><span data-stu-id="43c8c-153">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="43c8c-154">Cela permet de restaurer les packages des runtimes qui ne sont pas explicitement listés dans la balise `<RuntimeIdentifiers>` du fichier *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="43c8c-154">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="43c8c-155">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="43c8c-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="43c8c-156">Fournissez plusieurs identificateurs de runtime en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="43c8c-156">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="43c8c-157">Spécifie la source de package NuGet à utiliser pendant l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="43c8c-157">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="43c8c-158">Ce paramètre remplace toutes les sources spécifiées dans les fichiers *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="43c8c-158">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="43c8c-159">Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="43c8c-159">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="43c8c-160">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="43c8c-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="43c8c-161">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="43c8c-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="43c8c-162">La valeur par défaut est `minimal`.</span><span class="sxs-lookup"><span data-stu-id="43c8c-162">Default value is `minimal`.</span></span>

`--interactive`

<span data-ttu-id="43c8c-163">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’identifier).</span><span class="sxs-lookup"><span data-stu-id="43c8c-163">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="43c8c-164">Depuis .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="43c8c-164">Since .NET Core 2.1.400.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="43c8c-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="43c8c-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="43c8c-166">Fichier de configuration NuGet (*nuget.config*) à utiliser pour l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="43c8c-166">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="43c8c-167">Désactive la restauration de plusieurs projets en parallèle.</span><span class="sxs-lookup"><span data-stu-id="43c8c-167">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="43c8c-168">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="43c8c-168">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="43c8c-169">N’avertit en cas d’échec des sources que si des packages répondent aux exigences de versions.</span><span class="sxs-lookup"><span data-stu-id="43c8c-169">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="43c8c-170">Spécifie de ne pas mettre en cache les packages et les requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="43c8c-170">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="43c8c-171">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="43c8c-171">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="43c8c-172">Spécifie le répertoire des packages restaurés.</span><span class="sxs-lookup"><span data-stu-id="43c8c-172">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="43c8c-173">Spécifie un runtime pour la restauration du package.</span><span class="sxs-lookup"><span data-stu-id="43c8c-173">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="43c8c-174">Cela permet de restaurer les packages des runtimes qui ne sont pas explicitement listés dans la balise `<RuntimeIdentifiers>` du fichier *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="43c8c-174">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="43c8c-175">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="43c8c-175">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="43c8c-176">Fournissez plusieurs identificateurs de runtime en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="43c8c-176">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="43c8c-177">Spécifie la source de package NuGet à utiliser pendant l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="43c8c-177">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="43c8c-178">Cela remplace toutes les sources spécifiées dans les fichiers *NuGet. config* , en lisant le fichier *NuGet. config* comme si l’élément `<packageSource>` n’était pas là.</span><span class="sxs-lookup"><span data-stu-id="43c8c-178">This overrides all of the sources specified in the *nuget.config* files, effectively reading the *nuget.config* file as if the `<packageSource>` element was not there.</span></span> <span data-ttu-id="43c8c-179">Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="43c8c-179">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="43c8c-180">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="43c8c-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="43c8c-181">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="43c8c-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="43c8c-182">La valeur par défaut est `minimal`,</span><span class="sxs-lookup"><span data-stu-id="43c8c-182">The default is `minimal`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="43c8c-183">Exemples</span><span class="sxs-lookup"><span data-stu-id="43c8c-183">Examples</span></span>

<span data-ttu-id="43c8c-184">Restaurez des dépendances et des outils pour le projet se trouvant dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="43c8c-184">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="43c8c-185">Restaurez des dépendances et des outils pour le projet `app1` se trouvant à l’emplacement donné :</span><span class="sxs-lookup"><span data-stu-id="43c8c-185">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="43c8c-186">Restaurer les dépendances et les outils du projet se trouvant dans le répertoire actif en utilisant le chemin d’accès de fichier fourni comme source :</span><span class="sxs-lookup"><span data-stu-id="43c8c-186">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="43c8c-187">Restaurer les dépendances et les outils du projet se trouvant dans le répertoire actif en utilisant les deux chemins d’accès de fichiers fournis comme sources :</span><span class="sxs-lookup"><span data-stu-id="43c8c-187">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="43c8c-188">Restaurez les dépendances et les outils pour le projet dans le répertoire actif et affichez la sortie détaillée :</span><span class="sxs-lookup"><span data-stu-id="43c8c-188">Restore dependencies and tools for the project in the current directory showing detailed output:</span></span>

`dotnet restore --verbosity detailed`
