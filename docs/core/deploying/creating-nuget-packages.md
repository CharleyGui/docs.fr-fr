---
title: Créer un package NuGet avec la CLI .NET Core
description: Découvrez comment créer un package NuGet avec la commande « dotnet pack ».
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 3f8e75a501cfc48e1c416f71e91290cab1a4ffae
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920919"
---
# <a name="how-to-create-a-nuget-package-with-the-net-core-cli"></a><span data-ttu-id="3bc96-103">Comment créer un package NuGet avec la CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="3bc96-103">How to create a NuGet package with the .NET Core CLI</span></span>

> [!NOTE]
> <span data-ttu-id="3bc96-104">Voici des exemples de ligne de commande avec Unix.</span><span class="sxs-lookup"><span data-stu-id="3bc96-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="3bc96-105">La commande `dotnet pack` montrée ici fonctionne de la même façon sur Windows.</span><span class="sxs-lookup"><span data-stu-id="3bc96-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="3bc96-106">Les bibliothèques .NET Standard et .NET Core devraient être distribuées sous forme de packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="3bc96-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="3bc96-107">Il s’agit en fait de la façon dont toutes les bibliothèques .NET Standard sont distribuées et consommées.</span><span class="sxs-lookup"><span data-stu-id="3bc96-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="3bc96-108">Cette opération est plus facile avec la commande `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="3bc96-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="3bc96-109">Imaginez que vous venez d’écrire une nouvelle bibliothèque que vous voulez distribuer via NuGet.</span><span class="sxs-lookup"><span data-stu-id="3bc96-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="3bc96-110">Vous pouvez créer un package NuGet avec des outils multiplateformes pour effectuer cette opération.</span><span class="sxs-lookup"><span data-stu-id="3bc96-110">You can create a NuGet package with cross-platform tools to do exactly that!</span></span> <span data-ttu-id="3bc96-111">L’exemple suivant suppose une bibliothèque appelée **superawesomelibrary ciblant** qui cible `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="3bc96-111">The following example assumes a library called **SuperAwesomeLibrary** that targets `netstandard1.0`.</span></span>

<span data-ttu-id="3bc96-112">Si vous avez des dépendances transitives, c’est-à-dire un projet qui dépend d’un autre package, assurez-vous de restaurer les packages pour l’ensemble de la solution avec la commande `dotnet restore` avant de créer un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="3bc96-112">If you have transitive dependencies, that is, a project that depends on another package, make sure to restore packages for the entire solution with the `dotnet restore` command before you create a NuGet package.</span></span> <span data-ttu-id="3bc96-113">Si vous ne le faites pas, la commande `dotnet pack` ne fonctionnera pas correctement.</span><span class="sxs-lookup"><span data-stu-id="3bc96-113">Failing to do so will result in the `dotnet pack` command not working properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="3bc96-114">Après avoir vérifié que les packages sont restaurés, vous pouvez accéder au répertoire où se trouve une bibliothèque :</span><span class="sxs-lookup"><span data-stu-id="3bc96-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="3bc96-115">Il s’agit d’une seule commande à partir de la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="3bc96-115">Then it's just a single command from the command line:</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="3bc96-116">Votre dossier */bin/debug* ressemble maintenant à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="3bc96-116">Your */bin/Debug* folder will now look like this:</span></span>

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="3bc96-117">Cela produit un package pouvant être débogué.</span><span class="sxs-lookup"><span data-stu-id="3bc96-117">This produces a package that is capable of being debugged.</span></span> <span data-ttu-id="3bc96-118">Pour générer un package NuGet avec des fichiers binaires compilés, il suffit d’ajouter le commutateur `--configuration` (ou `-c`) et d’utiliser `release` comme argument.</span><span class="sxs-lookup"><span data-stu-id="3bc96-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```dotnetcli
dotnet pack --configuration release
```

<span data-ttu-id="3bc96-119">Votre dossier */bin* dispose désormais d’un dossier *Release* contenant votre package NuGet avec les fichiers binaires de mise en version :</span><span class="sxs-lookup"><span data-stu-id="3bc96-119">Your */bin* folder will now have a *release* folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="3bc96-120">Vous avez maintenant les fichiers nécessaires pour publier un package NuGet !</span><span class="sxs-lookup"><span data-stu-id="3bc96-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="3bc96-121">Ne confondez pas `dotnet pack` et `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="3bc96-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="3bc96-122">Il est important de noter qu’à aucun moment, la commande `dotnet publish` n’est impliquée.</span><span class="sxs-lookup"><span data-stu-id="3bc96-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="3bc96-123">La commande `dotnet publish` sert à déployer des applications avec toutes leurs dépendances dans le même bundle, et non pas à générer un package NuGet à distribuer et à consommer sur NuGet.</span><span class="sxs-lookup"><span data-stu-id="3bc96-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="3bc96-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bc96-124">See also</span></span>

- [<span data-ttu-id="3bc96-125">Démarrage rapide : Créer et publier un package</span><span class="sxs-lookup"><span data-stu-id="3bc96-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
