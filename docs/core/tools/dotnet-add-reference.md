---
title: commande dotnet Add Reference
description: La commande dotnet add reference est une option pratique pour ajouter des références entre projets.
ms.date: 02/14/2020
ms.openlocfilehash: b261e24ed6a9d5bd489d317d2663b1420b5c34ff
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158318"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="41ae3-103">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="41ae3-103">dotnet add reference</span></span>

<span data-ttu-id="41ae3-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="41ae3-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="41ae3-105">Nom</span><span class="sxs-lookup"><span data-stu-id="41ae3-105">Name</span></span>

<span data-ttu-id="41ae3-106">`dotnet add reference` : ajoute des références entre projets (P2P).</span><span class="sxs-lookup"><span data-stu-id="41ae3-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="41ae3-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="41ae3-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] reference [-f|--framework <FRAMEWORK>]
     [--interactive] <PROJECT_REFERENCES>

dotnet add reference -h|--help
```

## <a name="description"></a><span data-ttu-id="41ae3-108">Description</span><span class="sxs-lookup"><span data-stu-id="41ae3-108">Description</span></span>

<span data-ttu-id="41ae3-109">La commande `dotnet add reference` est une option pratique pour ajouter des références de projet à un projet.</span><span class="sxs-lookup"><span data-stu-id="41ae3-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="41ae3-110">Une fois que vous avez exécuté la commande, les éléments `<ProjectReference>` sont ajoutés au fichier projet.</span><span class="sxs-lookup"><span data-stu-id="41ae3-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="41ae3-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="41ae3-111">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="41ae3-112">Spécifie le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="41ae3-112">Specifies the project file.</span></span> <span data-ttu-id="41ae3-113">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="41ae3-113">If not specified, the command searches the current directory for one.</span></span>

- **`PROJECT_REFERENCES`**

  <span data-ttu-id="41ae3-114">Références entre projets (P2P) à ajouter.</span><span class="sxs-lookup"><span data-stu-id="41ae3-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="41ae3-115">Spécifiez un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="41ae3-115">Specify one or more projects.</span></span> <span data-ttu-id="41ae3-116">Les [modèles Glob](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les systèmes Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="41ae3-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="41ae3-117">Options</span><span class="sxs-lookup"><span data-stu-id="41ae3-117">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="41ae3-118">Ajoute des références de projet uniquement quand vous ciblez un [Framework](../../standard/frameworks.md) spécifique à l’aide du format TFM.</span><span class="sxs-lookup"><span data-stu-id="41ae3-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md) using the TFM format.</span></span>

- **`-h|--help`**

  <span data-ttu-id="41ae3-119">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="41ae3-119">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="41ae3-120">Permet à la commande de s’arrêter et d’attendre une entrée ou une action de l’utilisateur (généralement utilisée pour terminer l’authentification).</span><span class="sxs-lookup"><span data-stu-id="41ae3-120">Allows the command to stop and wait for user input or action (typically used to complete authentication).</span></span> <span data-ttu-id="41ae3-121">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="41ae3-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="41ae3-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="41ae3-122">Examples</span></span>

- <span data-ttu-id="41ae3-123">Ajouter une référence de projet :</span><span class="sxs-lookup"><span data-stu-id="41ae3-123">Add a project reference:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="41ae3-124">Ajouter plusieurs références de projet au projet dans le répertoire actuel :</span><span class="sxs-lookup"><span data-stu-id="41ae3-124">Add multiple project references to the project in the current directory:</span></span>

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="41ae3-125">Ajouter plusieurs références de projet à l’aide du modèle d’utilisation des caractères génériques (globbing) sur Linux/Unix :</span><span class="sxs-lookup"><span data-stu-id="41ae3-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
