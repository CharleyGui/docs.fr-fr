---
title: Commande dotnet restore
description: Découvrez comment restaurer les dépendances et les outils spécifiques du projet avec la commande dotnet restore.
ms.date: 02/27/2020
ms.openlocfilehash: c5cc9adf1d77b0ab03a61cc315d42c2f38362ad9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021773"
---
# <a name="dotnet-restore"></a><span data-ttu-id="4d2f1-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="4d2f1-103">dotnet restore</span></span>

<span data-ttu-id="4d2f1-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="4d2f1-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="4d2f1-105">Nom</span><span class="sxs-lookup"><span data-stu-id="4d2f1-105">Name</span></span>

<span data-ttu-id="4d2f1-106">`dotnet restore` : Restaure les dépendances et les outils d’un projet.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4d2f1-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="4d2f1-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="4d2f1-108">Description</span><span class="sxs-lookup"><span data-stu-id="4d2f1-108">Description</span></span>

<span data-ttu-id="4d2f1-109">La commande `dotnet restore` utilise NuGet pour restaurer les dépendances, ainsi que les outils spécifiques aux projets qui sont spécifiés dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="4d2f1-110">Par défaut, la restauration des dépendances et celle des outils sont exécutées en parallèle.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

<span data-ttu-id="4d2f1-111">Pour restaurer les dépendances, NuGet a besoin des flux où sont situés les packages.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-111">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="4d2f1-112">Les flux sont généralement fournis via le fichier de configuration *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-112">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="4d2f1-113">Un fichier de configuration par défaut est fourni lors de l’installation du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-113">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="4d2f1-114">Vous pouvez spécifier d’autres flux en créant votre propre fichier *nuget.config* dans le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-114">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="4d2f1-115">Vous pouvez remplacer les flux *nuget.config* avec `-s` l’option.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-115">You can override the *nuget.config* feeds with the - `-s` option.</span></span>

<span data-ttu-id="4d2f1-116">Pour les dépendances, vous pouvez spécifier l’emplacement des packages restaurés pendant l’opération de restauration à l’aide de l’argument `--packages`.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-116">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="4d2f1-117">Si aucune valeur n’est spécifiée, le cache du package NuGet par défaut est utilisé. Il se trouve dans le répertoire `.nuget/packages`, situé dans le répertoire de base de l’utilisateur, sur tous les systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-117">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="4d2f1-118">Par exemple, */home/user1* sur Linux ou *C:\Users\user1* sur Windows.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-118">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="4d2f1-119">Pour les outils spécifiques au projet, `dotnet restore` commence par restaurer le package dans lequel l’outil est empaqueté, puis il restaure les dépendances de l’outil, comme spécifié dans son fichier projet.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-119">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="4d2f1-120">Différences dans nuget.config</span><span class="sxs-lookup"><span data-stu-id="4d2f1-120">nuget.config differences</span></span>

<span data-ttu-id="4d2f1-121">Le comportement de la commande `dotnet restore` est affecté par les paramètres du fichier *nuget.config*, s’il est présent.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-121">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="4d2f1-122">Par exemple, si vous définissez `globalPackagesFolder` dans *nuget.config*, les packages NuGet restaurés sont placés dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-122">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="4d2f1-123">Cette méthode permet également de spécifier l’option `--packages` sur la commande `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="4d2f1-124">Pour plus d’informations, consultez [Informations de référence sur nuget.config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="4d2f1-124">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="4d2f1-125">Trois paramètres spécifiques sont ignorés par `dotnet restore` :</span><span class="sxs-lookup"><span data-stu-id="4d2f1-125">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="4d2f1-126">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="4d2f1-126">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="4d2f1-127">Les redirections de liaison ne fonctionnent pas avec les éléments `<PackageReference>` et .NET Core prend en charge seulement les éléments `<PackageReference>` pour les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-127">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="4d2f1-128">Solution</span><span class="sxs-lookup"><span data-stu-id="4d2f1-128">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="4d2f1-129">Ce paramètre est spécifique à Visual Studio et ne s’applique pas à .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-129">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="4d2f1-130">.NET Core n’utilise pas de fichier `packages.config` et utilise à la place des éléments `<PackageReference>` pour les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-130">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="4d2f1-131">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="4d2f1-131">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="4d2f1-132">Ce paramètre n’est pas applicable, car [NuGet ne prend pas encore en charge la vérification multiplateforme](https://github.com/NuGet/Home/issues/7939) des packages approuvés.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-132">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="4d2f1-133">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="4d2f1-133">Implicit restore</span></span>

<span data-ttu-id="4d2f1-134">La `dotnet restore` commande est exécutée implicitement si nécessaire lorsque vous exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4d2f1-134">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="4d2f1-135">Dans la plupart des cas, vous `dotnet restore` n’avez pas besoin d’utiliser explicitement la commande.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-135">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="4d2f1-136">Parfois, il peut s’avérer fastidieux d’exécuter `dotnet restore` implicitement.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-136">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="4d2f1-137">Par exemple, certains systèmes automatisés, comme les systèmes de génération, doivent appeler explicitement `dotnet restore` pour contrôler quand la restauration a lieu afin de pouvoir contrôler l’utilisation du réseau.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-137">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="4d2f1-138">Pour empêcher l’exécution implicite de `dotnet restore`, vous pouvez utiliser l’indicateur `--no-restore` avec l’une de ces commandes afin de désactiver la restauration implicite.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-138">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="4d2f1-139">Arguments</span><span class="sxs-lookup"><span data-stu-id="4d2f1-139">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="4d2f1-140">Chemin facultatif du fichier projet à restaurer.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-140">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="4d2f1-141">Options</span><span class="sxs-lookup"><span data-stu-id="4d2f1-141">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="4d2f1-142">Fichier de configuration NuGet (*nuget.config*) à utiliser pour l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-142">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="4d2f1-143">Désactive la restauration de plusieurs projets en parallèle.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-143">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="4d2f1-144">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-144">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="4d2f1-145">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-145">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="4d2f1-146">Les forces restaurent pour réévaluer toutes les dépendances même si un fichier de verrouillage existe déjà.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-146">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="4d2f1-147">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-147">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="4d2f1-148">N’avertit en cas d’échec des sources que si des packages répondent aux exigences de versions.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-148">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="4d2f1-149">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’identifier).</span><span class="sxs-lookup"><span data-stu-id="4d2f1-149">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="4d2f1-150">Depuis .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-150">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="4d2f1-151">Emplacement de sortie où le fichier de verrouillage du projet est écrit.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-151">Output location where project lock file is written.</span></span> <span data-ttu-id="4d2f1-152">Par défaut, il *s’agit de PROJECT_ROOT-packages.lock.json*.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-152">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="4d2f1-153">N’autorisez pas la mise à jour du fichier de verrouillage du projet.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-153">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="4d2f1-154">Spécifie de ne pas mettre en cache les demandes HTTP.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-154">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="4d2f1-155">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-155">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="4d2f1-156">Spécifie le répertoire des packages restaurés.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-156">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="4d2f1-157">Spécifie un runtime pour la restauration du package.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-157">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="4d2f1-158">Cela permet de restaurer les packages des runtimes qui ne sont pas explicitement listés dans la balise `<RuntimeIdentifiers>` du fichier *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-158">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="4d2f1-159">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="4d2f1-159">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="4d2f1-160">Fournissez plusieurs identificateurs de runtime en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-160">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="4d2f1-161">Spécifie la source de package NuGet à utiliser pendant l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-161">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="4d2f1-162">Ce paramètre remplace toutes les sources spécifiées dans les fichiers *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-162">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="4d2f1-163">Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-163">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lockfile`**

  <span data-ttu-id="4d2f1-164">Permet de générer et d’utiliser le fichier de verrouillage du projet lors de la restauration.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-164">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="4d2f1-165">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-165">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4d2f1-166">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-166">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4d2f1-167">La valeur par défaut est `minimal`.</span><span class="sxs-lookup"><span data-stu-id="4d2f1-167">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="4d2f1-168">Exemples</span><span class="sxs-lookup"><span data-stu-id="4d2f1-168">Examples</span></span>

- <span data-ttu-id="4d2f1-169">Restaurez des dépendances et des outils pour le projet se trouvant dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="4d2f1-169">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="4d2f1-170">Restaurer les dépendances et `app1` les outils du projet trouvé dans le chemin donné :</span><span class="sxs-lookup"><span data-stu-id="4d2f1-170">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="4d2f1-171">Restaurer les dépendances et les outils du projet dans l’annuaire actuel en utilisant le chemin de fichier fourni comme source :</span><span class="sxs-lookup"><span data-stu-id="4d2f1-171">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="4d2f1-172">Restaurer les dépendances et les outils du projet dans l’annuaire actuel en utilisant les deux voies de fichiers fournies comme sources :</span><span class="sxs-lookup"><span data-stu-id="4d2f1-172">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="4d2f1-173">Restaurer les dépendances et les outils du projet dans l’annuaire actuel montrant une sortie détaillée :</span><span class="sxs-lookup"><span data-stu-id="4d2f1-173">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
