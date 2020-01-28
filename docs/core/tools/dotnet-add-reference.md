---
title: commande dotnet Add Reference
description: La commande dotnet add reference est une option pratique pour ajouter des références entre projets.
ms.date: 06/26/2019
ms.openlocfilehash: dc8bc01a2bff4f2cf3a8af9efb233448d7de337f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733269"
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="ebc1a-103">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="ebc1a-103">dotnet add reference</span></span>

<span data-ttu-id="ebc1a-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 1. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="ebc1a-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="ebc1a-105">Name</span><span class="sxs-lookup"><span data-stu-id="ebc1a-105">Name</span></span>

<span data-ttu-id="ebc1a-106">`dotnet add reference` : ajoute des références entre projets (P2P).</span><span class="sxs-lookup"><span data-stu-id="ebc1a-106">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ebc1a-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="ebc1a-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a><span data-ttu-id="ebc1a-108">Description</span><span class="sxs-lookup"><span data-stu-id="ebc1a-108">Description</span></span>

<span data-ttu-id="ebc1a-109">La commande `dotnet add reference` est une option pratique pour ajouter des références de projet à un projet.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="ebc1a-110">Après l’exécution de la commande, les éléments `<ProjectReference>` sont ajoutés au fichier projet.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-110">After running the command, the `<ProjectReference>` elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="ebc1a-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="ebc1a-111">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="ebc1a-112">Spécifie le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-112">Specifies the project file.</span></span> <span data-ttu-id="ebc1a-113">Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-113">If not specified, the command searches the current directory for one.</span></span>

- **`PROJECT_REFERENCES`**

  <span data-ttu-id="ebc1a-114">Références entre projets (P2P) à ajouter.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="ebc1a-115">Spécifiez un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-115">Specify one or more projects.</span></span> <span data-ttu-id="ebc1a-116">Les [modèles Glob](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les systèmes Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="ebc1a-117">Options</span><span class="sxs-lookup"><span data-stu-id="ebc1a-117">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="ebc1a-118">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-118">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ebc1a-119">Ajoute des références de projet uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`--interactive`**

  <span data-ttu-id="ebc1a-120">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (son authentification, par exemple).</span><span class="sxs-lookup"><span data-stu-id="ebc1a-120">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="ebc1a-121">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ebc1a-121">Available since .NET Core 3.0 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="ebc1a-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="ebc1a-122">Examples</span></span>

- <span data-ttu-id="ebc1a-123">Ajouter une référence de projet :</span><span class="sxs-lookup"><span data-stu-id="ebc1a-123">Add a project reference:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="ebc1a-124">Ajouter plusieurs références de projet au projet dans le répertoire actuel :</span><span class="sxs-lookup"><span data-stu-id="ebc1a-124">Add multiple project references to the project in the current directory:</span></span>

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="ebc1a-125">Ajouter plusieurs références de projet à l’aide du modèle d’utilisation des caractères génériques (globbing) sur Linux/Unix :</span><span class="sxs-lookup"><span data-stu-id="ebc1a-125">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
