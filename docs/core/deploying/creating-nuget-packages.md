---
title: Créer un package NuGet avec des outils de l’interface de ligne de commande (CLI) de .NET Core
description: Découvrez comment créer un package NuGet avec la commande « dotnet pack ».
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: b86b2706968bf302a8421bcc8e12c32a97102e9e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632114"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a><span data-ttu-id="57f33-103">Guide pratique pour créer un package NuGet avec des outils de l’interface de ligne de commande (CLI) de .NET Core</span><span class="sxs-lookup"><span data-stu-id="57f33-103">How to create a NuGet package with .NET Core command-line interface (CLI) tools</span></span>

> [!NOTE]
> <span data-ttu-id="57f33-104">Voici des exemples de ligne de commande avec Unix.</span><span class="sxs-lookup"><span data-stu-id="57f33-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="57f33-105">La commande `dotnet pack` montrée ici fonctionne de la même façon sur Windows.</span><span class="sxs-lookup"><span data-stu-id="57f33-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="57f33-106">Les bibliothèques .NET Standard et .NET Core devraient être distribuées sous forme de packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="57f33-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="57f33-107">Il s’agit en fait de la façon dont toutes les bibliothèques .NET Standard sont distribuées et consommées.</span><span class="sxs-lookup"><span data-stu-id="57f33-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="57f33-108">Cette opération est plus facile avec la commande `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="57f33-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="57f33-109">Imaginez que vous venez d’écrire une nouvelle bibliothèque que vous voulez distribuer via NuGet.</span><span class="sxs-lookup"><span data-stu-id="57f33-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="57f33-110">Pour cela, vous pouvez créer un package NuGet avec les outils multiplateformes.</span><span class="sxs-lookup"><span data-stu-id="57f33-110">You can create a NuGet package with cross platform tools to do exactly that!</span></span> <span data-ttu-id="57f33-111">L’exemple suivant suppose une bibliothèque nommée **SuperAwesomeLibrary** ciblant `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="57f33-111">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="57f33-112">Si vous avez des dépendances transitives (c’est-à-dire un projet qui dépend d’un autre package), veillez à restaurer les packages de l’ensemble de votre solution avec la commande `dotnet restore` avant de créer un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="57f33-112">If you have transitive dependencies; that is, a project which depends on another package, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span> <span data-ttu-id="57f33-113">Si vous ne le faites pas, la commande `dotnet pack` ne fonctionne pas correctement.</span><span class="sxs-lookup"><span data-stu-id="57f33-113">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="57f33-114">Après avoir vérifié que les packages sont restaurés, vous pouvez accéder au répertoire où se trouve une bibliothèque :</span><span class="sxs-lookup"><span data-stu-id="57f33-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="57f33-115">Il s’agit d’une seule commande à partir de la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="57f33-115">Then it's just a single command from the command line:</span></span>

```console
dotnet pack
```

<span data-ttu-id="57f33-116">Votre dossier `/bin/Debug` doit maintenant ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="57f33-116">Your `/bin/Debug` folder will now look like this:</span></span>

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="57f33-117">Notez que ceci génère un package qui peut être débogué.</span><span class="sxs-lookup"><span data-stu-id="57f33-117">Note that this will produce a package which is capable of being debugged.</span></span> <span data-ttu-id="57f33-118">Pour générer un package NuGet avec des fichiers binaires compilés, il suffit d’ajouter le commutateur `--configuration` (ou `-c`) et d’utiliser `release` comme argument.</span><span class="sxs-lookup"><span data-stu-id="57f33-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```console
dotnet pack --configuration release
```

<span data-ttu-id="57f33-119">Votre dossier `/bin` a désormais un dossier `release` contenant votre package NuGet avec les fichiers binaires compilés :</span><span class="sxs-lookup"><span data-stu-id="57f33-119">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="57f33-120">Vous avez maintenant les fichiers nécessaires pour publier un package NuGet !</span><span class="sxs-lookup"><span data-stu-id="57f33-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="57f33-121">Ne confondez pas `dotnet pack` et `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="57f33-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="57f33-122">Il est important de noter qu’à aucun moment, la commande `dotnet publish` n’est impliquée.</span><span class="sxs-lookup"><span data-stu-id="57f33-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="57f33-123">La commande `dotnet publish` sert à déployer des applications avec toutes leurs dépendances dans le même bundle, et non pas à générer un package NuGet à distribuer et à consommer sur NuGet.</span><span class="sxs-lookup"><span data-stu-id="57f33-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="57f33-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57f33-124">See also</span></span>

- [<span data-ttu-id="57f33-125">Démarrage rapide : Créer et publier un package</span><span class="sxs-lookup"><span data-stu-id="57f33-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
