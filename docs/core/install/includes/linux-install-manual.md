---
ms.openlocfilehash: ea2883912907843e4b6d65db5ba186af43f27aaa
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85805774"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="04474-101">Comme alternative aux gestionnaires de packages, vous pouvez télécharger et installer manuellement le kit de développement logiciel (SDK) et le Runtime.</span><span class="sxs-lookup"><span data-stu-id="04474-101">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="04474-102">L’installation manuelle est généralement effectuée dans le cadre du test d’intégration continue ou sur une distribution Linux non prise en charge.</span><span class="sxs-lookup"><span data-stu-id="04474-102">Manual install is usually performed as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="04474-103">Pour un développeur ou un utilisateur, il est généralement préférable d’utiliser un gestionnaire de package.</span><span class="sxs-lookup"><span data-stu-id="04474-103">For a developer or user, it's generally better to use a package manager.</span></span>

<span data-ttu-id="04474-104">Si vous installez kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="04474-104">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="04474-105">Tout d’abord, téléchargez une version **binaire** pour le kit de développement logiciel (SDK) ou le runtime à partir de l’un des sites suivants :</span><span class="sxs-lookup"><span data-stu-id="04474-105">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="04474-106">Téléchargements de ✔️ [.net 5,0 Preview](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="04474-106">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="04474-107">✔️ [téléchargements .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="04474-107">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="04474-108">✔️ [téléchargements .net Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="04474-108">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="04474-109">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="04474-109">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="04474-110">Ensuite, extrayez le fichier téléchargé et utilisez la `export` commande pour définir les variables utilisées par .net Core, puis vérifiez que .net Core se trouve dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="04474-110">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="04474-111">Pour extraire le runtime et rendre les commandes CLI .NET Core disponibles sur le terminal, commencez par télécharger une version binaire .NET Core.</span><span class="sxs-lookup"><span data-stu-id="04474-111">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="04474-112">Ensuite, ouvrez un terminal et exécutez les commandes suivantes à partir du répertoire dans lequel le fichier a été enregistré.</span><span class="sxs-lookup"><span data-stu-id="04474-112">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="04474-113">Le nom du fichier d’archive peut être différent en fonction de ce que vous avez téléchargé.</span><span class="sxs-lookup"><span data-stu-id="04474-113">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="04474-114">**Utilisez la commande suivante pour extraire le runtime**:</span><span class="sxs-lookup"><span data-stu-id="04474-114">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="04474-115">**Utilisez la commande suivante pour extraire le kit de développement logiciel (SDK)**:</span><span class="sxs-lookup"><span data-stu-id="04474-115">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="04474-116">Les `export` commandes précédentes rendent uniquement les commandes CLI .net Core disponibles pour la session Terminal dans laquelle elles ont été exécutées.</span><span class="sxs-lookup"><span data-stu-id="04474-116">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="04474-117">Vous pouvez modifier votre profil de Shell pour ajouter définitivement les commandes.</span><span class="sxs-lookup"><span data-stu-id="04474-117">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="04474-118">Un certain nombre de shells différents sont disponibles pour Linux et chacun d’eux a un profil différent.</span><span class="sxs-lookup"><span data-stu-id="04474-118">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="04474-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="04474-119">For example:</span></span>
>
> - <span data-ttu-id="04474-120">**Interpréteur**de commandes bash : *~/. bash_profile*, *~ fichier/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="04474-120">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="04474-121">**Shell Korn**: *~/.kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="04474-121">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="04474-122">**Z Shell**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="04474-122">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="04474-123">Modifiez le fichier source approprié pour votre shell et ajoutez `:$HOME/dotnet` à la fin de l' `PATH` instruction existante.</span><span class="sxs-lookup"><span data-stu-id="04474-123">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="04474-124">Si aucune `PATH` instruction n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="04474-124">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="04474-125">Ajoutez également `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="04474-125">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="04474-126">Cette approche vous permet d’installer différentes versions dans des emplacements distincts et de choisir explicitement celle qui doit être utilisée par l’application.</span><span class="sxs-lookup"><span data-stu-id="04474-126">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>
