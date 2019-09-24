---
title: Utilisation de Package Management F# avec pour Azure
description: Utiliser Paket ou NuGet pour gérer F# les dépendances Azure
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 4aa32ace91f30d0e43b9c40067f5f0f456cc4069
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214230"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="025c9-103">Gestion des packages pour les dépendances F# Azure</span><span class="sxs-lookup"><span data-stu-id="025c9-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="025c9-104">L’obtention de packages pour le développement Azure est facile lorsque vous utilisez un gestionnaire de package.</span><span class="sxs-lookup"><span data-stu-id="025c9-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="025c9-105">Les deux options sont [Paket](https://fsprojects.github.io/Paket/) et [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="025c9-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="025c9-106">Utilisation de Paket</span><span class="sxs-lookup"><span data-stu-id="025c9-106">Using Paket</span></span>

<span data-ttu-id="025c9-107">Si vous utilisez [Paket](https://fsprojects.github.io/Paket/) comme gestionnaire de dépendances, vous pouvez utiliser l' `paket.exe` outil pour ajouter des dépendances Azure.</span><span class="sxs-lookup"><span data-stu-id="025c9-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="025c9-108">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="025c9-108">For example:</span></span>

```console
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="025c9-109">Ou, si vous utilisez [mono](https://www.mono-project.com/) pour le développement .net multiplateforme :</span><span class="sxs-lookup"><span data-stu-id="025c9-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="025c9-110">Cela ajoute `WindowsAzure.Storage` à votre ensemble de dépendances de package pour le projet dans le répertoire actif, modifie `paket.dependencies` le fichier et télécharge le package.</span><span class="sxs-lookup"><span data-stu-id="025c9-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="025c9-111">Si vous avez déjà configuré des dépendances ou si vous travaillez avec un projet dans lequel des dépendances ont été configurées par un autre développeur, vous pouvez résoudre et installer les dépendances localement comme suit :</span><span class="sxs-lookup"><span data-stu-id="025c9-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> paket install
```

<span data-ttu-id="025c9-112">Ou, pour le développement mono :</span><span class="sxs-lookup"><span data-stu-id="025c9-112">Or, for Mono development:</span></span>

```console
> mono paket.exe install
```

<span data-ttu-id="025c9-113">Vous pouvez mettre à jour toutes les dépendances de votre package avec la version la plus récente, comme suit :</span><span class="sxs-lookup"><span data-stu-id="025c9-113">You can update all your package dependencies to the latest version like this:</span></span>

```console
> paket update
```

<span data-ttu-id="025c9-114">Ou, pour le développement mono :</span><span class="sxs-lookup"><span data-stu-id="025c9-114">Or, for Mono development:</span></span>

```console
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="025c9-115">Utilisation de NuGet</span><span class="sxs-lookup"><span data-stu-id="025c9-115">Using Nuget</span></span>

<span data-ttu-id="025c9-116">Si vous utilisez [NuGet](https://www.nuget.org/) comme gestionnaire de dépendances, vous pouvez utiliser l' `nuget.exe` outil pour ajouter des dépendances Azure.</span><span class="sxs-lookup"><span data-stu-id="025c9-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="025c9-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="025c9-117">For example:</span></span>

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="025c9-118">Ou, pour le développement mono :</span><span class="sxs-lookup"><span data-stu-id="025c9-118">Or, for Mono development:</span></span>

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="025c9-119">Cela ajoutera `WindowsAzure.Storage` à votre ensemble de dépendances de package pour le projet dans le répertoire actif et téléchargera le package.</span><span class="sxs-lookup"><span data-stu-id="025c9-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="025c9-120">Si vous avez déjà configuré des dépendances ou si vous travaillez avec un projet dans lequel des dépendances ont été configurées par un autre développeur, vous pouvez résoudre et installer les dépendances localement comme suit :</span><span class="sxs-lookup"><span data-stu-id="025c9-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> nuget restore
```

<span data-ttu-id="025c9-121">Ou, pour le développement mono :</span><span class="sxs-lookup"><span data-stu-id="025c9-121">Or, for Mono development:</span></span>

```console
> mono nuget.exe restore
```

<span data-ttu-id="025c9-122">Vous pouvez mettre à jour toutes les dépendances de votre package avec la version la plus récente, comme suit :</span><span class="sxs-lookup"><span data-stu-id="025c9-122">You can update all your package dependencies to the latest version like this:</span></span>

```console
> nuget update
```

<span data-ttu-id="025c9-123">Ou, pour le développement mono :</span><span class="sxs-lookup"><span data-stu-id="025c9-123">Or, for Mono development:</span></span>

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="025c9-124">Référencement d'assemblys</span><span class="sxs-lookup"><span data-stu-id="025c9-124">Referencing Assemblies</span></span>

<span data-ttu-id="025c9-125">Pour pouvoir utiliser vos packages dans votre F# script, vous devez référencer les assemblys inclus dans les packages à l’aide `#r` d’une directive.</span><span class="sxs-lookup"><span data-stu-id="025c9-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="025c9-126">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="025c9-126">For example:</span></span>

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="025c9-127">Comme vous pouvez le voir, vous devez spécifier le chemin d’accès relatif à la DLL et le nom complet de la DLL, qui peut ne pas être exactement le même que le nom du package.</span><span class="sxs-lookup"><span data-stu-id="025c9-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="025c9-128">Le chemin d’accès inclut une version de Framework et éventuellement un numéro de version de package.</span><span class="sxs-lookup"><span data-stu-id="025c9-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="025c9-129">Pour rechercher tous les assemblys installés, vous pouvez utiliser une commande semblable à celle-ci sur une ligne de commande Windows :</span><span class="sxs-lookup"><span data-stu-id="025c9-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="025c9-130">Ou dans un interpréteur de commandes UNIX, comme suit :</span><span class="sxs-lookup"><span data-stu-id="025c9-130">Or in a Unix shell, something like this:</span></span>

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="025c9-131">Vous obtiendrez les chemins d’accès aux assemblys installés.</span><span class="sxs-lookup"><span data-stu-id="025c9-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="025c9-132">À partir de là, vous pouvez sélectionner le chemin d’accès correct pour la version de votre infrastructure.</span><span class="sxs-lookup"><span data-stu-id="025c9-132">From there, you can select the correct path for your framework version.</span></span>
