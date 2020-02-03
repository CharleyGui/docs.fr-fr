---
title: Commande dotnet add package
description: La commande « dotnet add package » est une option pratique pour ajouter une référence de package NuGet à un projet.
ms.date: 06/26/2019
ms.openlocfilehash: 210dcf0efe06672264ebfa297589bdb387591a42
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733331"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="4a1eb-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="4a1eb-103">dotnet add package</span></span>

<span data-ttu-id="4a1eb-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 1. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="4a1eb-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="4a1eb-105">Nom</span><span class="sxs-lookup"><span data-stu-id="4a1eb-105">Name</span></span>

<span data-ttu-id="4a1eb-106">`dotnet add package` : Ajoute une référence de package à un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4a1eb-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="4a1eb-107">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="4a1eb-108">Description</span><span class="sxs-lookup"><span data-stu-id="4a1eb-108">Description</span></span>

<span data-ttu-id="4a1eb-109">La commande `dotnet add package` est une option pratique pour ajouter une référence de package à un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="4a1eb-110">Une fois que vous avez exécuté la commande, il existe un contrôle de compatibilité qui vérifie que le package est compatible avec les frameworks du projet.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="4a1eb-111">Si le résultat du contrôle est positif, un élément `<PackageReference>` est ajouté au fichier projet et la commande [dotnet restore](dotnet-restore.md) est exécutée.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="4a1eb-112">Par exemple, l’ajout de `Newtonsoft.Json` à *ToDo.csproj* produit une sortie similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4a1eb-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
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

<span data-ttu-id="4a1eb-113">Le fichier *ToDo.csproj* contient à présent un élément [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) pour le package référencé.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="4a1eb-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="4a1eb-114">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="4a1eb-115">Spécifie le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-115">Specifies the project file.</span></span> <span data-ttu-id="4a1eb-116">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-116">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="4a1eb-117">Référence de package à ajouter.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="4a1eb-118">Options</span><span class="sxs-lookup"><span data-stu-id="4a1eb-118">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="4a1eb-119">Ajoute une référence de package uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="4a1eb-120">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-120">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="4a1eb-121">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (son authentification, par exemple).</span><span class="sxs-lookup"><span data-stu-id="4a1eb-121">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="4a1eb-122">Disponible à partir du kit SDK .NET Core 2.1, version 2.1.400 (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="4a1eb-122">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="4a1eb-123">Ajoute une référence de package sans effectuer d’aperçu de restauration ni de contrôle de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-123">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="4a1eb-124">Répertoire où restaurer les packages.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-124">The directory where to restore the packages.</span></span> <span data-ttu-id="4a1eb-125">L’emplacement de restauration de package par défaut est `%userprofile%\.nuget\packages` sur Windows, et `~/.nuget/packages` sur macOS et Linux.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-125">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="4a1eb-126">Pour plus d’informations, consultez [Gérer les dossiers de packages globaux, les dossiers de cache et les dossiers temporaires dans NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="4a1eb-126">For more information, see [Managing the global packages, cache, and temp folders in NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="4a1eb-127">Source de package NuGet à utiliser pendant l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-127">The NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="4a1eb-128">Version du package.</span><span class="sxs-lookup"><span data-stu-id="4a1eb-128">Version of the package.</span></span> <span data-ttu-id="4a1eb-129">Consultez [Contrôle de version du package NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="4a1eb-129">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="4a1eb-130">Exemples</span><span class="sxs-lookup"><span data-stu-id="4a1eb-130">Examples</span></span>

- <span data-ttu-id="4a1eb-131">Ajouter un package NuGet `Newtonsoft.Json` à un projet :</span><span class="sxs-lookup"><span data-stu-id="4a1eb-131">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="4a1eb-132">Ajouter une version spécifique d’un package à un projet :</span><span class="sxs-lookup"><span data-stu-id="4a1eb-132">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="4a1eb-133">Ajouter un package à l’aide d’une source NuGet spécifique :</span><span class="sxs-lookup"><span data-stu-id="4a1eb-133">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="4a1eb-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a1eb-134">See also</span></span>

- [<span data-ttu-id="4a1eb-135">Gestion des dossiers de packages globaux, des dossiers de cache et des dossiers temporaires dans NuGet</span><span class="sxs-lookup"><span data-stu-id="4a1eb-135">Managing the global packages, cache, and temp folders in NuGet</span></span>](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="4a1eb-136">Gestion des versions des packages NuGet</span><span class="sxs-lookup"><span data-stu-id="4a1eb-136">NuGet package versioning</span></span>](https://docs.microsoft.com/nuget/reference/package-versioning)
