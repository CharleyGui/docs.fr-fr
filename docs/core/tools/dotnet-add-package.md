---
title: Commande dotnet add package
description: La commande « dotnet add package » est une option pratique pour ajouter une référence de package NuGet à un projet.
ms.date: 02/14/2020
ms.openlocfilehash: 1d57aed59ccd45417c88f9b6a2f9dd768fda9b58
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102851"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="83d3f-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="83d3f-103">dotnet add package</span></span>

<span data-ttu-id="83d3f-104">**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="83d3f-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="83d3f-105">Nom</span><span class="sxs-lookup"><span data-stu-id="83d3f-105">Name</span></span>

<span data-ttu-id="83d3f-106">`dotnet add package` : Ajoute une référence de package à un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="83d3f-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="83d3f-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="83d3f-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a><span data-ttu-id="83d3f-108">Description</span><span class="sxs-lookup"><span data-stu-id="83d3f-108">Description</span></span>

<span data-ttu-id="83d3f-109">La commande `dotnet add package` est une option pratique pour ajouter une référence de package à un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="83d3f-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="83d3f-110">Une fois que vous avez exécuté la commande, il existe un contrôle de compatibilité qui vérifie que le package est compatible avec les frameworks du projet.</span><span class="sxs-lookup"><span data-stu-id="83d3f-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="83d3f-111">Si le résultat du contrôle est positif, un élément `<PackageReference>` est ajouté au fichier projet et la commande [dotnet restore](dotnet-restore.md) est exécutée.</span><span class="sxs-lookup"><span data-stu-id="83d3f-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

<span data-ttu-id="83d3f-112">Par exemple, l’ajout de `Newtonsoft.Json` à *ToDo.csproj* produit une sortie similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="83d3f-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```console
Writing C:\Users\me\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="83d3f-113">Le fichier *ToDo.csproj* contient à présent un élément [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) pour le package référencé.</span><span class="sxs-lookup"><span data-stu-id="83d3f-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a><span data-ttu-id="83d3f-114">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="83d3f-114">Implicit restore</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="83d3f-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="83d3f-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="83d3f-116">Spécifie le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="83d3f-116">Specifies the project file.</span></span> <span data-ttu-id="83d3f-117">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="83d3f-117">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="83d3f-118">Référence de package à ajouter.</span><span class="sxs-lookup"><span data-stu-id="83d3f-118">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="83d3f-119">Options</span><span class="sxs-lookup"><span data-stu-id="83d3f-119">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="83d3f-120">Ajoute une référence de package uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="83d3f-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="83d3f-121">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="83d3f-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="83d3f-122">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (son authentification, par exemple).</span><span class="sxs-lookup"><span data-stu-id="83d3f-122">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="83d3f-123">Disponible à partir du kit SDK .NET Core 2.1, version 2.1.400 (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="83d3f-123">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="83d3f-124">Ajoute une référence de package sans effectuer d’aperçu de restauration ni de contrôle de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="83d3f-124">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="83d3f-125">Répertoire où restaurer les packages.</span><span class="sxs-lookup"><span data-stu-id="83d3f-125">The directory where to restore the packages.</span></span> <span data-ttu-id="83d3f-126">L’emplacement de restauration de package par défaut est `%userprofile%\.nuget\packages` sur Windows, et `~/.nuget/packages` sur macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="83d3f-126">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="83d3f-127">Pour plus d’informations, consultez [Gérer les dossiers de packages globaux, les dossiers de cache et les dossiers temporaires dans NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="83d3f-127">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="83d3f-128">Source de package NuGet à utiliser pendant l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="83d3f-128">The NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="83d3f-129">Version du package.</span><span class="sxs-lookup"><span data-stu-id="83d3f-129">Version of the package.</span></span> <span data-ttu-id="83d3f-130">Consultez [Contrôle de version du package NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="83d3f-130">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="83d3f-131">Exemples</span><span class="sxs-lookup"><span data-stu-id="83d3f-131">Examples</span></span>

- <span data-ttu-id="83d3f-132">Ajouter un package NuGet `Newtonsoft.Json` à un projet :</span><span class="sxs-lookup"><span data-stu-id="83d3f-132">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="83d3f-133">Ajouter une version spécifique d’un package à un projet :</span><span class="sxs-lookup"><span data-stu-id="83d3f-133">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="83d3f-134">Ajouter un package à l’aide d’une source NuGet spécifique :</span><span class="sxs-lookup"><span data-stu-id="83d3f-134">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="83d3f-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83d3f-135">See also</span></span>

- [<span data-ttu-id="83d3f-136">Gestion des dossiers de packages globaux, des dossiers de cache et des dossiers temporaires dans NuGet</span><span class="sxs-lookup"><span data-stu-id="83d3f-136">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="83d3f-137">Gestion des versions des packages NuGet</span><span class="sxs-lookup"><span data-stu-id="83d3f-137">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
