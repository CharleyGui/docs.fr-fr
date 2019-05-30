---
title: Commande dotnet add package
description: La commande « dotnet add package » est une option pratique pour ajouter une référence de package NuGet à un projet.
ms.date: 04/24/2019
ms.openlocfilehash: 82f178026b46eb0237243b8ae49d17fbcc1af6ec
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959242"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="9a02f-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="9a02f-103">dotnet add package</span></span>

<span data-ttu-id="9a02f-104">**Cet article s’applique à : ✓** SDK .NET Core 1.x et ultérieur</span><span class="sxs-lookup"><span data-stu-id="9a02f-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="9a02f-105">Name</span><span class="sxs-lookup"><span data-stu-id="9a02f-105">Name</span></span>

<span data-ttu-id="9a02f-106">`dotnet add package` : Ajoute une référence de package à un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="9a02f-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9a02f-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="9a02f-107">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="9a02f-108">Description</span><span class="sxs-lookup"><span data-stu-id="9a02f-108">Description</span></span>

<span data-ttu-id="9a02f-109">La commande `dotnet add package` est une option pratique pour ajouter une référence de package à un fichier projet.</span><span class="sxs-lookup"><span data-stu-id="9a02f-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="9a02f-110">Une fois que vous avez exécuté la commande, il existe un contrôle de compatibilité qui vérifie que le package est compatible avec les frameworks du projet.</span><span class="sxs-lookup"><span data-stu-id="9a02f-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="9a02f-111">Si le résultat du contrôle est positif, un élément `<PackageReference>` est ajouté au fichier projet et la commande [dotnet restore](dotnet-restore.md) est exécutée.</span><span class="sxs-lookup"><span data-stu-id="9a02f-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="9a02f-112">Par exemple, l’ajout de `Newtonsoft.Json` à *ToDo.csproj* produit une sortie similaire à l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="9a02f-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

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

<span data-ttu-id="9a02f-113">Le fichier *ToDo.csproj* contient à présent un élément [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) pour le package référencé.</span><span class="sxs-lookup"><span data-stu-id="9a02f-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="9a02f-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="9a02f-114">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="9a02f-115">Spécifie le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="9a02f-115">Specifies the project file.</span></span> <span data-ttu-id="9a02f-116">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="9a02f-116">If not specified, the command searches the current directory for one.</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="9a02f-117">Référence de package à ajouter.</span><span class="sxs-lookup"><span data-stu-id="9a02f-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="9a02f-118">Options</span><span class="sxs-lookup"><span data-stu-id="9a02f-118">Options</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9a02f-119">Ajoute une référence de package uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="9a02f-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

* **`-h|--help`**

  <span data-ttu-id="9a02f-120">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="9a02f-120">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="9a02f-121">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’authentifier).</span><span class="sxs-lookup"><span data-stu-id="9a02f-121">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="9a02f-122">Disponible à partir du kit SDK .NET Core 2.1, version 2.1.400 (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="9a02f-122">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

* **`-n|--no-restore`**

  <span data-ttu-id="9a02f-123">Ajoute une référence de package sans effectuer d’aperçu de restauration ni de contrôle de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="9a02f-123">Adds a package reference without performing a restore preview and compatibility check.</span></span>

* **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="9a02f-124">Répertoire où restaurer les packages.</span><span class="sxs-lookup"><span data-stu-id="9a02f-124">The directory where to restore the packages.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="9a02f-125">Source de package NuGet à utiliser pendant l’opération de restauration.</span><span class="sxs-lookup"><span data-stu-id="9a02f-125">The NuGet package source to use during the restore operation.</span></span>

* **`-v|--version <VERSION>`**

  <span data-ttu-id="9a02f-126">Version du package.</span><span class="sxs-lookup"><span data-stu-id="9a02f-126">Version of the package.</span></span> <span data-ttu-id="9a02f-127">Consultez [Contrôle de version du package NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="9a02f-127">See [NuGet package versioning](https://docs.microsoft.com/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="9a02f-128">Exemples</span><span class="sxs-lookup"><span data-stu-id="9a02f-128">Examples</span></span>

* <span data-ttu-id="9a02f-129">Ajouter un package NuGet `Newtonsoft.Json` à un projet :</span><span class="sxs-lookup"><span data-stu-id="9a02f-129">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```console
  dotnet add package Newtonsoft.Json
  ```

* <span data-ttu-id="9a02f-130">Ajouter une version spécifique d’un package à un projet :</span><span class="sxs-lookup"><span data-stu-id="9a02f-130">Add a specific version of a package to a project:</span></span>

  ```console
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

* <span data-ttu-id="9a02f-131">Ajouter un package à l’aide d’une source NuGet spécifique :</span><span class="sxs-lookup"><span data-stu-id="9a02f-131">Add a package using a specific NuGet source:</span></span>

  ```console
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```
