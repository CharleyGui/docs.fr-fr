---
title: Commande dotnet restore
description: Découvrez comment restaurer les dépendances et les outils spécifiques du projet avec la commande dotnet restore.
ms.date: 02/27/2020
ms.openlocfilehash: dcb68d6c690f2e12b61cfdfa6dc288bd474721c1
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634401"
---
# <a name="dotnet-restore"></a><span data-ttu-id="02108-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="02108-103">dotnet restore</span></span>

<span data-ttu-id="02108-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="02108-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="02108-105">Name</span><span class="sxs-lookup"><span data-stu-id="02108-105">Name</span></span>

<span data-ttu-id="02108-106">`dotnet restore` : Restaure les dépendances et les outils d’un projet.</span><span class="sxs-lookup"><span data-stu-id="02108-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="02108-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="02108-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lock-file] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="02108-108">Description</span><span class="sxs-lookup"><span data-stu-id="02108-108">Description</span></span>

<span data-ttu-id="02108-109">La commande `dotnet restore` utilise NuGet pour restaurer les dépendances, ainsi que les outils spécifiques aux projets qui sont spécifiés dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="02108-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span>  <span data-ttu-id="02108-110">Dans la plupart des cas, vous n’avez pas besoin d’utiliser explicitement la `dotnet restore` commande, car une restauration NuGet est exécutée implicitement si nécessaire lorsque vous exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="02108-110">In most cases, you don't need to explicitly use the `dotnet restore` command, since a NuGet restore is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="02108-111">Parfois, il peut être gênant d’exécuter la restauration NuGet implicite avec ces commandes.</span><span class="sxs-lookup"><span data-stu-id="02108-111">Sometimes, it might be inconvenient to run the implicit NuGet restore with these commands.</span></span> <span data-ttu-id="02108-112">Par exemple, certains systèmes automatisés, comme les systèmes de génération, doivent appeler explicitement `dotnet restore` pour contrôler quand la restauration a lieu afin de pouvoir contrôler l’utilisation du réseau.</span><span class="sxs-lookup"><span data-stu-id="02108-112">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="02108-113">Pour empêcher la restauration NuGet implicite, vous pouvez utiliser l' `--no-restore` indicateur avec l’une de ces commandes pour désactiver la restauration implicite.</span><span class="sxs-lookup"><span data-stu-id="02108-113">To prevent the implicit NuGet restore, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="02108-114">Spécifier les flux</span><span class="sxs-lookup"><span data-stu-id="02108-114">Specify feeds</span></span>

<span data-ttu-id="02108-115">Pour restaurer les dépendances, NuGet a besoin des flux où sont situés les packages.</span><span class="sxs-lookup"><span data-stu-id="02108-115">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="02108-116">Les flux sont généralement fournis via le fichier de configuration *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="02108-116">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="02108-117">Un fichier de configuration par défaut est fourni lorsque le kit de développement logiciel (SDK) .NET est installé.</span><span class="sxs-lookup"><span data-stu-id="02108-117">A default configuration file is provided when the .NET SDK is installed.</span></span> <span data-ttu-id="02108-118">Pour spécifier des flux supplémentaires, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="02108-118">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="02108-119">Créez votre propre *nuget.config* fichier dans le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="02108-119">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="02108-120">Pour plus d’informations, consultez [configurations NuGet courantes](/nuget/consume-packages/configuring-nuget-behavior) et [nuget.config différences](#nugetconfig-differences) plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="02108-120">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="02108-121">Utilisez des `dotnet nuget` commandes telles que [`dotnet nuget add source`](dotnet-nuget-add-source.md) .</span><span class="sxs-lookup"><span data-stu-id="02108-121">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="02108-122">Vous pouvez substituer les flux de *nuget.config* avec l' `-s` option.</span><span class="sxs-lookup"><span data-stu-id="02108-122">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="02108-123">Pour plus d’informations sur l’utilisation des flux authentifiés, consultez [utilisation de packages à partir de flux authentifiés](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span><span class="sxs-lookup"><span data-stu-id="02108-123">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="global-packages-folder"></a><span data-ttu-id="02108-124">Dossier de packages globaux</span><span class="sxs-lookup"><span data-stu-id="02108-124">Global packages folder</span></span>

<span data-ttu-id="02108-125">Pour les dépendances, vous pouvez spécifier l’emplacement des packages restaurés pendant l’opération de restauration à l’aide de l’argument `--packages`.</span><span class="sxs-lookup"><span data-stu-id="02108-125">For dependencies, you can specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="02108-126">Si aucune valeur n’est spécifiée, le cache du package NuGet par défaut est utilisé. Il se trouve dans le répertoire `.nuget/packages`, situé dans le répertoire de base de l’utilisateur, sur tous les systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="02108-126">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="02108-127">Par exemple, */home/user1* sur Linux ou *C:\Users\user1* sur Windows.</span><span class="sxs-lookup"><span data-stu-id="02108-127">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="02108-128">Outils spécifiques au projet</span><span class="sxs-lookup"><span data-stu-id="02108-128">Project-specific tooling</span></span>

<span data-ttu-id="02108-129">Pour les outils spécifiques au projet, `dotnet restore` commence par restaurer le package dans lequel l’outil est empaqueté, puis il restaure les dépendances de l’outil, comme spécifié dans son fichier projet.</span><span class="sxs-lookup"><span data-stu-id="02108-129">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="02108-130">Différences dans nuget.config</span><span class="sxs-lookup"><span data-stu-id="02108-130">nuget.config differences</span></span>

<span data-ttu-id="02108-131">Le comportement de la commande `dotnet restore` est affecté par les paramètres du fichier *nuget.config* , s’il est présent.</span><span class="sxs-lookup"><span data-stu-id="02108-131">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="02108-132">Par exemple, si vous définissez `globalPackagesFolder` dans *nuget.config* , les packages NuGet restaurés sont placés dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="02108-132">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="02108-133">Cette méthode permet également de spécifier l’option `--packages` sur la commande `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="02108-133">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="02108-134">Pour plus d’informations, consultez [Informations de référence sur nuget.config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="02108-134">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="02108-135">Trois paramètres spécifiques sont ignorés par `dotnet restore` :</span><span class="sxs-lookup"><span data-stu-id="02108-135">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="02108-136">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="02108-136">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="02108-137">Les redirections de liaison ne fonctionnent pas avec les `<PackageReference>` éléments et .net ne prend en charge que `<PackageReference>` les éléments des packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="02108-137">Binding redirects don't work with `<PackageReference>` elements and .NET only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="02108-138">Solution</span><span class="sxs-lookup"><span data-stu-id="02108-138">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="02108-139">Ce paramètre est spécifique à Visual Studio et ne s’applique pas à .NET.</span><span class="sxs-lookup"><span data-stu-id="02108-139">This setting is Visual Studio specific and doesn't apply to .NET.</span></span> <span data-ttu-id="02108-140">.NET n’utilise pas de `packages.config` fichier et utilise `<PackageReference>` à la place des éléments pour les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="02108-140">.NET doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="02108-141">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="02108-141">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="02108-142">Ce paramètre n’est pas applicable, car [NuGet ne prend pas encore en charge la vérification multiplateforme](https://github.com/NuGet/Home/issues/7939) des packages approuvés.</span><span class="sxs-lookup"><span data-stu-id="02108-142">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="arguments"></a><span data-ttu-id="02108-143">Arguments</span><span class="sxs-lookup"><span data-stu-id="02108-143">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="02108-144">Chemin facultatif du fichier projet à restaurer.</span><span class="sxs-lookup"><span data-stu-id="02108-144">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="02108-145">Options</span><span class="sxs-lookup"><span data-stu-id="02108-145">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="02108-146">Fichier de configuration NuGet ( *nuget.config* ) à utiliser pour l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="02108-146">The NuGet configuration file ( *nuget.config* ) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="02108-147">Désactive la restauration de plusieurs projets en parallèle.</span><span class="sxs-lookup"><span data-stu-id="02108-147">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="02108-148">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="02108-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="02108-149">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="02108-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="02108-150">Force la restauration à réévaluer toutes les dépendances même si un fichier de verrouillage existe déjà.</span><span class="sxs-lookup"><span data-stu-id="02108-150">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="02108-151">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="02108-151">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="02108-152">N’avertit en cas d’échec des sources que si des packages répondent aux exigences de versions.</span><span class="sxs-lookup"><span data-stu-id="02108-152">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="02108-153">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’identifier).</span><span class="sxs-lookup"><span data-stu-id="02108-153">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="02108-154">Depuis .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="02108-154">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="02108-155">Emplacement de sortie où le fichier de verrouillage de projet est écrit.</span><span class="sxs-lookup"><span data-stu-id="02108-155">Output location where project lock file is written.</span></span> <span data-ttu-id="02108-156">Par défaut, il s’agit *dePROJECT_ROOT\packages.lock.js*.</span><span class="sxs-lookup"><span data-stu-id="02108-156">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="02108-157">N’autorise pas la mise à jour du fichier de verrouillage de projet.</span><span class="sxs-lookup"><span data-stu-id="02108-157">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="02108-158">Spécifie de ne pas mettre en cache les requêtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="02108-158">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="02108-159">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="02108-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="02108-160">Spécifie le répertoire des packages restaurés.</span><span class="sxs-lookup"><span data-stu-id="02108-160">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="02108-161">Spécifie un runtime pour la restauration du package.</span><span class="sxs-lookup"><span data-stu-id="02108-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="02108-162">Cela permet de restaurer les packages des runtimes qui ne sont pas explicitement listés dans la balise `<RuntimeIdentifiers>` du fichier *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="02108-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="02108-163">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="02108-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="02108-164">Fournissez plusieurs identificateurs de runtime en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="02108-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="02108-165">Spécifie l’URI de la source de package NuGet à utiliser pendant l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="02108-165">Specifies the URI of the NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="02108-166">Ce paramètre remplace toutes les sources spécifiées dans les fichiers *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="02108-166">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="02108-167">Vous pouvez spécifier plusieurs sources en spécifiant cette option plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="02108-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lock-file`**

  <span data-ttu-id="02108-168">Active la génération et l’utilisation du fichier de verrouillage de projet avec Restore.</span><span class="sxs-lookup"><span data-stu-id="02108-168">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="02108-169">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="02108-169">Sets the verbosity level of the command.</span></span> <span data-ttu-id="02108-170">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="02108-170">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="02108-171">La valeur par défaut est `minimal`.</span><span class="sxs-lookup"><span data-stu-id="02108-171">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="02108-172">Exemples</span><span class="sxs-lookup"><span data-stu-id="02108-172">Examples</span></span>

- <span data-ttu-id="02108-173">Restaurez des dépendances et des outils pour le projet se trouvant dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="02108-173">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="02108-174">Restaurez des dépendances et des outils pour le projet `app1` se trouvant à l’emplacement donné :</span><span class="sxs-lookup"><span data-stu-id="02108-174">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

  ```dotnetcli
  dotnet restore ./projects/app1/app1.csproj
  ```

- <span data-ttu-id="02108-175">Restaurez les dépendances et les outils pour le projet dans le répertoire actif à l’aide du chemin d’accès de fichier fourni comme source :</span><span class="sxs-lookup"><span data-stu-id="02108-175">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="02108-176">Restaurez les dépendances et les outils pour le projet dans le répertoire actif à l’aide des deux chemins d’accès de fichier fournis comme sources :</span><span class="sxs-lookup"><span data-stu-id="02108-176">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="02108-177">Restaurez les dépendances et les outils pour le projet dans le répertoire actif et affichez la sortie détaillée :</span><span class="sxs-lookup"><span data-stu-id="02108-177">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
