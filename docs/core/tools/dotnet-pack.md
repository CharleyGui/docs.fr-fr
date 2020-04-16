---
title: Commande dotnet pack
description: La commande dotnet pack crée des packages NuGet pour votre projet .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 3b9c46ecd5d67519728896b0018e27fb41ebd861
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463509"
---
# <a name="dotnet-pack"></a><span data-ttu-id="32994-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="32994-103">dotnet pack</span></span>

<span data-ttu-id="32994-104">**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="32994-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="32994-105">Nom</span><span class="sxs-lookup"><span data-stu-id="32994-105">Name</span></span>

<span data-ttu-id="32994-106">`dotnet pack` : Place le code dans un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="32994-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="32994-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="32994-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a><span data-ttu-id="32994-108">Description</span><span class="sxs-lookup"><span data-stu-id="32994-108">Description</span></span>

<span data-ttu-id="32994-109">La commande `dotnet pack` génère le projet et crée les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="32994-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="32994-110">Le résultat de cette commande est un paquet NuGet (c’est-à-dire un fichier *.nupkg).*</span><span class="sxs-lookup"><span data-stu-id="32994-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="32994-111">Si vous souhaitez générer un paquet contenant les symboles de débogé, vous avez deux options disponibles :</span><span class="sxs-lookup"><span data-stu-id="32994-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="32994-112">`--include-symbols`- il crée le paquet de symboles.</span><span class="sxs-lookup"><span data-stu-id="32994-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="32994-113">`--include-source`- il crée le `src` paquet de symboles avec un dossier à l’intérieur contenant les fichiers source.</span><span class="sxs-lookup"><span data-stu-id="32994-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="32994-114">Les dépendances NuGet du projet empaqueté sont ajoutées dans le fichier  *.nuspec*, pour pouvoir être correctement résolues lors de l’installation du package.</span><span class="sxs-lookup"><span data-stu-id="32994-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="32994-115">Les références entre projets ne sont pas empaquetées à l’intérieur du projet.</span><span class="sxs-lookup"><span data-stu-id="32994-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="32994-116">Actuellement, vous devez disposer d’un package par projet si vous avez des dépendances entre projets.</span><span class="sxs-lookup"><span data-stu-id="32994-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="32994-117">Par défaut, `dotnet pack` génère d’abord le projet.</span><span class="sxs-lookup"><span data-stu-id="32994-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="32994-118">Pour éviter ce comportement, passez l’option `--no-build`.</span><span class="sxs-lookup"><span data-stu-id="32994-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="32994-119">Cette option s’avère souvent utile dans les scénarios de build d’intégration continue (CI), pour lesquels vous savez que le code a déjà été créé.</span><span class="sxs-lookup"><span data-stu-id="32994-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

> [!NOTE]
> <span data-ttu-id="32994-120">Dans certains cas, la construction implicite ne peut pas être effectuée.</span><span class="sxs-lookup"><span data-stu-id="32994-120">In some cases, the implicit build cannot be performed.</span></span> <span data-ttu-id="32994-121">Cela peut `GeneratePackageOnBuild` se produire lorsque vous êtes réglé, pour éviter une dépendance cyclique entre les cibles de construction et de pack.</span><span class="sxs-lookup"><span data-stu-id="32994-121">This can occur when `GeneratePackageOnBuild` is set, to avoid a cyclic dependency between build and pack targets.</span></span> <span data-ttu-id="32994-122">La construction peut également échouer s’il y a un fichier verrouillé ou un autre problème.</span><span class="sxs-lookup"><span data-stu-id="32994-122">The build can also fail if there is a locked file or other issue.</span></span>

<span data-ttu-id="32994-123">Vous pouvez fournir des propriétés MSBuild à la commande `dotnet pack` pour le processus de compression.</span><span class="sxs-lookup"><span data-stu-id="32994-123">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="32994-124">Pour plus d’informations, consultez [Propriétés des métadonnées NuGet](csproj.md#nuget-metadata-properties) et [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="32994-124">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="32994-125">La section [Exemples](#examples) montre comment utiliser le commutateur MSBuild -p pour deux scénarios différents.</span><span class="sxs-lookup"><span data-stu-id="32994-125">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="32994-126">Par défaut, les projets web ne peuvent pas être ajoutés dans un package.</span><span class="sxs-lookup"><span data-stu-id="32994-126">Web projects aren't packable by default.</span></span> <span data-ttu-id="32994-127">Pour remplacer le comportement par défaut, ajoutez la propriété suivante à votre fichier *.csproj* :</span><span class="sxs-lookup"><span data-stu-id="32994-127">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="32994-128">Arguments</span><span class="sxs-lookup"><span data-stu-id="32994-128">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="32994-129">Le projet ou la solution à emballer.</span><span class="sxs-lookup"><span data-stu-id="32994-129">The project or solution to pack.</span></span> <span data-ttu-id="32994-130">C’est soit un chemin vers un [fichier csproj,](csproj.md)un fichier de solution, ou à un répertoire.</span><span class="sxs-lookup"><span data-stu-id="32994-130">It's either a path to a [csproj file](csproj.md), a solution file, or to a directory.</span></span> <span data-ttu-id="32994-131">S’il n’est pas précisé, la commande recherche l’annuaire actuel pour un projet ou un fichier de solution.</span><span class="sxs-lookup"><span data-stu-id="32994-131">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="32994-132">Options</span><span class="sxs-lookup"><span data-stu-id="32994-132">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="32994-133">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="32994-133">Defines the build configuration.</span></span> <span data-ttu-id="32994-134">La valeur par `Debug`défaut pour la plupart des projets est, mais vous pouvez remplacer les paramètres de configuration de construction dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="32994-134">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="32994-135">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="32994-135">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="32994-136">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="32994-136">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="32994-137">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="32994-137">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="32994-138">Inclut les symboles de débopathie NuGet paquets en plus des paquets NuGet régulière dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="32994-138">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="32994-139">Les fichiers sources sont `src` inclus dans le dossier dans le paquet de symboles.</span><span class="sxs-lookup"><span data-stu-id="32994-139">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="32994-140">Inclut les symboles de débopathie NuGet paquets en plus des paquets NuGet régulière dans le répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="32994-140">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="32994-141">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (son authentification, par exemple).</span><span class="sxs-lookup"><span data-stu-id="32994-141">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="32994-142">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="32994-142">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="32994-143">Ne génère pas le projet avant de créer le package.</span><span class="sxs-lookup"><span data-stu-id="32994-143">Doesn't build the project before packing.</span></span> <span data-ttu-id="32994-144">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="32994-144">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="32994-145">Ignore les références entre projets et restaure uniquement le projet racine.</span><span class="sxs-lookup"><span data-stu-id="32994-145">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="32994-146">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="32994-146">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="32994-147">N’affiche pas la bannière de démarrage ni le message de copyright.</span><span class="sxs-lookup"><span data-stu-id="32994-147">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="32994-148">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="32994-148">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="32994-149">Place les packages générés dans le répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="32994-149">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="32994-150">Spécifie le runtime cible pour lequel restaurer les packages.</span><span class="sxs-lookup"><span data-stu-id="32994-150">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="32994-151">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="32994-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="32994-152">Définit l’indicateur d’un état pouvant faire l’objet d’une maintenance dans le package.</span><span class="sxs-lookup"><span data-stu-id="32994-152">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="32994-153">Pour plus d’informations, consultez [Blog .NET : .NET 4.5.1 prend en charge les mises à jour de sécurité de Microsoft pour les bibliothèques NuGet .NET](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="32994-153">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="32994-154">Définit la valeur de la propriété MSBuild `$(VersionSuffix)` dans le projet.</span><span class="sxs-lookup"><span data-stu-id="32994-154">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="32994-155">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="32994-155">Sets the verbosity level of the command.</span></span> <span data-ttu-id="32994-156">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="32994-156">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="32994-157">Exemples</span><span class="sxs-lookup"><span data-stu-id="32994-157">Examples</span></span>

- <span data-ttu-id="32994-158">Empaquetez le projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="32994-158">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="32994-159">Empaqueter le projet `app1` :</span><span class="sxs-lookup"><span data-stu-id="32994-159">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="32994-160">Empaqueter le projet dans le répertoire actif et placer les packages résultants dans le dossier `nupkgs` :</span><span class="sxs-lookup"><span data-stu-id="32994-160">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="32994-161">Empaqueter le projet dans le répertoire actif du dossier `nupkgs` et ignorer l’étape de génération :</span><span class="sxs-lookup"><span data-stu-id="32994-161">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="32994-162">Avec le suffixe de version du projet configuré comme `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` dans le fichier *.csproj*, empaqueter le projet actif et mettre à jour la version du package obtenue avec le suffixe donné :</span><span class="sxs-lookup"><span data-stu-id="32994-162">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="32994-163">Affectez `2.1.0` à la version du package à l’aide de la propriété MSBuild `PackageVersion` :</span><span class="sxs-lookup"><span data-stu-id="32994-163">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="32994-164">Empaquetez le projet pour un [framework cible](../../standard/frameworks.md) spécifique :</span><span class="sxs-lookup"><span data-stu-id="32994-164">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="32994-165">Emballez le projet et utilisez un temps d’exécution spécifique (Windows 10) pour l’opération de restauration :</span><span class="sxs-lookup"><span data-stu-id="32994-165">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="32994-166">Empaquetez le projet à l’aide d’un [fichier .nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec) :</span><span class="sxs-lookup"><span data-stu-id="32994-166">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
