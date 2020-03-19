---
title: Installer F#
description: Apprenez à installer le Fmd de différentes façons.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400245"
---
# <a name="install-f"></a><span data-ttu-id="b110a-103">Installer F\#</span><span class="sxs-lookup"><span data-stu-id="b110a-103">Install F\#</span></span>

<span data-ttu-id="b110a-104">Vous pouvez installer F de multiples façons, en fonction de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="b110a-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="b110a-105">Installer FMD avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b110a-105">Install F# with Visual Studio</span></span>

1. <span data-ttu-id="b110a-106">Si vous téléchargez [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pour la première fois, il installera d’abord Visual Studio Install.</span><span class="sxs-lookup"><span data-stu-id="b110a-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for the first time, it will first install Visual Studio Installer.</span></span> <span data-ttu-id="b110a-107">Installez l’édition appropriée de Visual Studio à partir de l’installateur.</span><span class="sxs-lookup"><span data-stu-id="b110a-107">Install the appropriate edition of Visual Studio from the installer.</span></span>

   <span data-ttu-id="b110a-108">Si vous avez déjà Visual Studio installé, choisissez **Modifier** à côté de l’édition que vous souhaitez ajouter F ' à.</span><span class="sxs-lookup"><span data-stu-id="b110a-108">If you already have Visual Studio installed, choose **Modify** next to the edition you want to add F# to.</span></span>

2. <span data-ttu-id="b110a-109">Sur la page Charges de travail, sélectionnez la charge de travail **de ASP.NET et de développement Web,** qui comprend le support de base de F et .NET pour ASP.NET projets de base.</span><span class="sxs-lookup"><span data-stu-id="b110a-109">On the Workloads page, select the **ASP.NET and web development** workload, which includes F# and .NET Core support for ASP.NET Core projects.</span></span>

3. <span data-ttu-id="b110a-110">Choisissez **Modifier** dans le coin inférieur droit pour installer tout ce que vous avez sélectionné.</span><span class="sxs-lookup"><span data-stu-id="b110a-110">Choose **Modify** in the lower right-hand corner to install everything you've selected.</span></span>

   <span data-ttu-id="b110a-111">Vous pouvez ensuite ouvrir Visual Studio avec Fmd en choisissant **Launch** in Visual Studio Install.</span><span class="sxs-lookup"><span data-stu-id="b110a-111">You can then open Visual Studio with F# by choosing **Launch** in Visual Studio Installer.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="b110a-112">Installer FMD avec code visual studio</span><span class="sxs-lookup"><span data-stu-id="b110a-112">Install F# with Visual Studio Code</span></span>

1. <span data-ttu-id="b110a-113">Assurez-vous d’avoir [git](https://git-scm.com/download) installé et disponible sur votre PATH.</span><span class="sxs-lookup"><span data-stu-id="b110a-113">Ensure you have [git](https://git-scm.com/download) installed and available on your PATH.</span></span> <span data-ttu-id="b110a-114">Vous pouvez vérifier qu’il est `git --version` installé correctement en entrant à une invite de commande et en appuyant **sur Enter**.</span><span class="sxs-lookup"><span data-stu-id="b110a-114">You can verify that it's installed correctly by entering `git --version` at a command prompt and pressing **Enter**.</span></span>

2. <span data-ttu-id="b110a-115">Installez le [code SDK core et](https://dotnet.microsoft.com/download) Visual Studio [.NET](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="b110a-115">Install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com).</span></span>

3. <span data-ttu-id="b110a-116">Sélectionnez l’icône Extensions et recherchez "Ionide":</span><span class="sxs-lookup"><span data-stu-id="b110a-116">Select the Extensions icon and search for "Ionide":</span></span>

   <span data-ttu-id="b110a-117">Le seul plugin requis pour le support F dans Visual Studio Code est [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="b110a-117">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="b110a-118">Cependant, vous pouvez également installer [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) pour obtenir le support [FAKE](https://fake.build/) et [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) pour obtenir le soutien [de Paket.](https://fsprojects.github.io/Paket/)</span><span class="sxs-lookup"><span data-stu-id="b110a-118">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="b110a-119">FAKE et Paket sont des outils communautaires supplémentaires pour la construction de projets et la gestion des dépendances, respectivement.</span><span class="sxs-lookup"><span data-stu-id="b110a-119">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="b110a-120">Installer F AVEC Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="b110a-120">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="b110a-121">F est installé par défaut dans [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), quelle que soit la configuration que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="b110a-121">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="b110a-122">Une fois l’installation terminée, choisissez **Start Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b110a-122">After the install completes, choose **Start Visual Studio**.</span></span> <span data-ttu-id="b110a-123">Vous pouvez également ouvrir Visual Studio via Finder sur macOS.</span><span class="sxs-lookup"><span data-stu-id="b110a-123">You can also open Visual Studio through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="b110a-124">Installer F sur un serveur de construction</span><span class="sxs-lookup"><span data-stu-id="b110a-124">Install F# on a build server</span></span>

<span data-ttu-id="b110a-125">Si vous utilisez .NET Core ou .NET Framework via le .NET SDK, vous avez simplement besoin d’installer le .NET SDK sur votre serveur de construction.</span><span class="sxs-lookup"><span data-stu-id="b110a-125">If you're using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="b110a-126">Il a tout ce dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="b110a-126">It has everything you need.</span></span>

<span data-ttu-id="b110a-127">Si vous utilisez .NET Framework et que vous **n’utilisez pas** le .NET SDK, vous devrez installer les outils de construction de studio [visuel SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) sur votre serveur Windows.</span><span class="sxs-lookup"><span data-stu-id="b110a-127">If you're using .NET Framework and you are **not** using the .NET SDK, then you'll need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="b110a-128">Dans l’installateur, sélectionnez des **outils de construction de bureau .NET,** puis sélectionnez le composant **compilateur F sur** le côté droit du menu de l’installateur.</span><span class="sxs-lookup"><span data-stu-id="b110a-128">In the installer, select **.NET desktop build tools**, and then select the **F# compiler** component on the right-hand side of the installer menu.</span></span>
