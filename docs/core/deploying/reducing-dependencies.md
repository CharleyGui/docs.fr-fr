---
title: Réduction des dépendances de package avec project.json
description: Réduisez les dépendances de package dans le cadre de la création de bibliothèques project.json.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740828"
---
# <a name="reducing-package-dependencies-with-projectjson"></a><span data-ttu-id="d7483-103">Réduction des dépendances de package avec project.json</span><span class="sxs-lookup"><span data-stu-id="d7483-103">Reducing Package Dependencies with project.json</span></span>

<span data-ttu-id="d7483-104">Cet article décrit ce que vous devez savoir sur la réduction de vos dépendances de package lors de la création de bibliothèques `project.json`.</span><span class="sxs-lookup"><span data-stu-id="d7483-104">This article covers what you need to know about reducing your package dependencies when authoring `project.json` libraries.</span></span> <span data-ttu-id="d7483-105">À la fin de cet article, vous saurez comment composer votre bibliothèque de sorte qu’elle utilise seulement les dépendances dont elle a besoin.</span><span class="sxs-lookup"><span data-stu-id="d7483-105">By the end of this article, you will learn how to compose your library such that it only uses the dependencies it needs.</span></span>

## <a name="why-its-important"></a><span data-ttu-id="d7483-106">Pourquoi c’est important</span><span class="sxs-lookup"><span data-stu-id="d7483-106">Why it's Important</span></span>

<span data-ttu-id="d7483-107">.NET Core est un produit composé de packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="d7483-107">.NET Core is a product made up of NuGet packages.</span></span>  <span data-ttu-id="d7483-108">Parmi les packages essentiels figure le [métapackage .NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library), un package NuGet composé d’autres packages.</span><span class="sxs-lookup"><span data-stu-id="d7483-108">An essential package is the [.NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), which is a NuGet package composed of other packages.</span></span> <span data-ttu-id="d7483-109">Il vous fournit l’ensemble de paquets qui sont garantis pour travailler sur plusieurs implémentations .NET, tels que .NET Framework, .NET Core, et Xamarin/Mono.</span><span class="sxs-lookup"><span data-stu-id="d7483-109">It provides you with the set of packages that are guaranteed to work on multiple .NET implementations, such as .NET Framework, .NET Core, and Xamarin/Mono.</span></span>

<span data-ttu-id="d7483-110">Cependant, il est probable que votre bibliothèque n’utilise pas chaque package individuel qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="d7483-110">However, there's a good chance that your library won't use every single package it contains.</span></span>  <span data-ttu-id="d7483-111">Lors de la création d’une bibliothèque et de sa distribution sur NuGet, il est conseillé de « réduire » vos dépendances aux seuls packages que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="d7483-111">When authoring a library and distributing it over NuGet, it's a best practice to "trim" your dependencies down to only the packages you actually use.</span></span>  <span data-ttu-id="d7483-112">Ceci aboutit à un encombrement global inférieur pour les packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="d7483-112">This results in a smaller overall footprint for NuGet packages.</span></span>

## <a name="how-to-do-it"></a><span data-ttu-id="d7483-113">Marche à suivre</span><span class="sxs-lookup"><span data-stu-id="d7483-113">How to do it</span></span>

<span data-ttu-id="d7483-114">Actuellement, il n’y a pas de commande officielle `dotnet` qui coupe les références de paquet.</span><span class="sxs-lookup"><span data-stu-id="d7483-114">Currently, there is no official `dotnet` command that trims package references.</span></span>  <span data-ttu-id="d7483-115">Vous devez donc le faire manuellement.</span><span class="sxs-lookup"><span data-stu-id="d7483-115">Instead, you'll have to do it manually.</span></span>  <span data-ttu-id="d7483-116">Le processus général se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="d7483-116">The general process looks like the following:</span></span>

1. <span data-ttu-id="d7483-117">Faites référence à `NETStandard.Library` version `1.6.0` dans une section `dependencies` de votre fichier `project.json`.</span><span class="sxs-lookup"><span data-stu-id="d7483-117">Reference `NETStandard.Library` version `1.6.0` in a `dependencies` section of your `project.json`.</span></span>
2. <span data-ttu-id="d7483-118">Restaurez les packages avec `dotnet restore` ([voir la remarque](#dotnet-restore-note)) à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d7483-118">Restore packages with `dotnet restore` ([see note](#dotnet-restore-note)) from the command line.</span></span>
3. <span data-ttu-id="d7483-119">Parcourez le fichier `project.lock.json` et recherchez la section `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="d7483-119">Inspect the `project.lock.json` file and find the `NETStandard.Library` section.</span></span>  <span data-ttu-id="d7483-120">Elle est au début du fichier.</span><span class="sxs-lookup"><span data-stu-id="d7483-120">It's near the beginning of the file.</span></span>
4. <span data-ttu-id="d7483-121">Copiez tous les packages répertoriés sous `dependencies`.</span><span class="sxs-lookup"><span data-stu-id="d7483-121">Copy all of the listed packages under `dependencies`.</span></span>
5. <span data-ttu-id="d7483-122">Supprimez la référence à `.NETStandard.Library` et remplacez-la par les packages copiés.</span><span class="sxs-lookup"><span data-stu-id="d7483-122">Remove the `.NETStandard.Library` reference and replace it with the copied packages.</span></span>
6. <span data-ttu-id="d7483-123">Supprimez les références aux packages dont vous n’avez pas besoin.</span><span class="sxs-lookup"><span data-stu-id="d7483-123">Remove references to packages you don't need.</span></span>

<span data-ttu-id="d7483-124">Vous pouvez déterminer les packages dont vous n’avez pas besoin de l’une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="d7483-124">You can find out which packages you don't need by one of the following ways:</span></span>

1. <span data-ttu-id="d7483-125">Essai et erreur.</span><span class="sxs-lookup"><span data-stu-id="d7483-125">Trial and error.</span></span> <span data-ttu-id="d7483-126">Ceci implique de supprimer un package, de le restaurer, de déterminer si votre bibliothèque se compile encore et de répéter ce processus.</span><span class="sxs-lookup"><span data-stu-id="d7483-126">This involves removing a package, restoring, seeing if your library still compiles, and repeating this process.</span></span>
2. <span data-ttu-id="d7483-127">L’utilisation d’un outil comme [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) ou [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) permet d’examiner les références pour voir ce que votre code utilise réellement.</span><span class="sxs-lookup"><span data-stu-id="d7483-127">Using a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector) to peek at references to see what your code is actually using.</span></span> <span data-ttu-id="d7483-128">Vous pouvez ensuite supprimer les paquets qui ne correspondent pas aux types que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="d7483-128">You can then remove packages that don't correspond to types you're using.</span></span>

## <a name="example"></a><span data-ttu-id="d7483-129"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d7483-129">Example</span></span>

<span data-ttu-id="d7483-130">Imaginez que vous avez écrit une bibliothèque qui fournissait des fonctionnalités supplémentaires aux types de collecte génériques.</span><span class="sxs-lookup"><span data-stu-id="d7483-130">Imagine that you wrote a library that provided additional functionality to generic collection types.</span></span> <span data-ttu-id="d7483-131">Ce type de bibliothèque doit dépendre de packages comme `System.Collections`, mais peut ne pas du tout dépendre de packages comme `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="d7483-131">Such a library would need to depend on packages such as `System.Collections`, but may not at all depend on packages such as `System.Net.Http`.</span></span> <span data-ttu-id="d7483-132">Par conséquent, il serait judicieux de réduire les dépendances des packages aux seuls packages dont cette bibliothèque a besoin !</span><span class="sxs-lookup"><span data-stu-id="d7483-132">As such, it would be good to trim package dependencies down to only what this library required!</span></span>

<span data-ttu-id="d7483-133">Pour réduire cette bibliothèque, vous commencez par le fichier `project.json` et vous ajoutez une référence à `NETStandard.Library` version `1.6.0`.</span><span class="sxs-lookup"><span data-stu-id="d7483-133">To trim this library, you start with the `project.json` file and add a reference to `NETStandard.Library` version `1.6.0`.</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="d7483-134">Ensuite, vous restaurez les packages avec `dotnet restore` ([voir la remarque](#dotnet-restore-note)), vous examinez le fichier `project.lock.json` et vous recherchez tous les packages restaurés pour `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="d7483-134">Next, you restore packages with `dotnet restore` ([see note](#dotnet-restore-note)), inspect the `project.lock.json` file, and find all the packages restored for `NETStandard.Library`.</span></span>

<span data-ttu-id="d7483-135">Voici à quoi ressemble la section appropriée du fichier `project.lock.json` quand vous ciblez `netstandard1.0` :</span><span class="sxs-lookup"><span data-stu-id="d7483-135">Here's what the relevant section in the `project.lock.json` file looks like when targeting `netstandard1.0`:</span></span>

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

<span data-ttu-id="d7483-136">Ensuite, copiez les références de package dans la section `dependencies` du fichier `project.json` de la bibliothèque, en remplaçant la référence `NETStandard.Library` :</span><span class="sxs-lookup"><span data-stu-id="d7483-136">Next, copy over the package references into the `dependencies` section of the library's `project.json` file, replacing the `NETStandard.Library` reference:</span></span>

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

<span data-ttu-id="d7483-137">Cela représente beaucoup de packages, dont la plupart ne sont certainement pas nécessaires pour étendre les types de collections.</span><span class="sxs-lookup"><span data-stu-id="d7483-137">That's quite a lot of packages, many of which certainly aren't necessary for extending collection types.</span></span>  <span data-ttu-id="d7483-138">Vous pouvez supprimer manuellement les packages ou utiliser un outil comme [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) ou [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) pour identifier les packages utilisés par votre code.</span><span class="sxs-lookup"><span data-stu-id="d7483-138">You can either remove packages manually or use a tool such as [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) or [.NET Reflector](https://www.red-gate.com/products/dotnet-development/reflector/) to identify which packages your code actually uses.</span></span>

<span data-ttu-id="d7483-139">Voici ce à quoi un package réduit peut ressembler :</span><span class="sxs-lookup"><span data-stu-id="d7483-139">Here's what a trimmed package could look like:</span></span>

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

<span data-ttu-id="d7483-140">Il a maintenant un encombrement moindre que s’il dépendait du métapackage `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="d7483-140">Now, it has a smaller footprint than if it had depended on the `NETStandard.Library` metapackage.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
