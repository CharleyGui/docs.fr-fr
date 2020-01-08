---
title: Installer F#
description: Découvrez comment procéder à F# l’installation de différentes façons.
ms.date: 12/20/2019
ms.openlocfilehash: 302e04f7cf3271516dff88d9d5f18f620b6ede80
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346567"
---
# <a name="install-f"></a><span data-ttu-id="a4a8e-103">Installer F\#</span><span class="sxs-lookup"><span data-stu-id="a4a8e-103">Install F\#</span></span>

<span data-ttu-id="a4a8e-104">Vous pouvez installer F# de plusieurs façons, en fonction de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="a4a8e-105">Installer F# avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a4a8e-105">Install F# with Visual Studio</span></span>

1. <span data-ttu-id="a4a8e-106">Si vous téléchargez [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) pour la première fois, vous devez d’abord installer Visual Studio installer.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) for the first time, it will first install Visual Studio Installer.</span></span> <span data-ttu-id="a4a8e-107">Installez l’édition appropriée de Visual Studio à partir du programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-107">Install the appropriate edition of Visual Studio from the installer.</span></span>

   <span data-ttu-id="a4a8e-108">Si vous avez déjà installé Visual Studio, choisissez **modifier** en regard de l’édition que vous souhaitez F# ajouter à.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-108">If you already have Visual Studio installed, choose **Modify** next to the edition you want to add F# to.</span></span>

2. <span data-ttu-id="a4a8e-109">Sur la page charges de travail, sélectionnez la charge de travail **développement ASP.net et Web** , qui comprend F# la prise en charge de .net Core pour les projets ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-109">On the Workloads page, select the **ASP.NET and web development** workload, which includes F# and .NET Core support for ASP.NET Core projects.</span></span>

3. <span data-ttu-id="a4a8e-110">Choisissez **modifier** dans le coin inférieur droit pour installer tout ce que vous avez sélectionné.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-110">Choose **Modify** in the lower right-hand corner to install everything you've selected.</span></span>

   <span data-ttu-id="a4a8e-111">Vous pouvez ensuite ouvrir Visual Studio avec F# en choisissant **lancer** dans Visual Studio installer.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-111">You can then open Visual Studio with F# by choosing **Launch** in Visual Studio Installer.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="a4a8e-112">Installer F# avec Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="a4a8e-112">Install F# with Visual Studio Code</span></span>

1. <span data-ttu-id="a4a8e-113">Vérifiez que [git](https://git-scm.com/download) est installé et disponible sur votre chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-113">Ensure you have [git](https://git-scm.com/download) installed and available on your PATH.</span></span> <span data-ttu-id="a4a8e-114">Vous pouvez vérifier qu’il est correctement installé en entrant `git --version` à l’invite de commandes et en appuyant sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-114">You can verify that it's installed correctly by entering `git --version` at a command prompt and pressing **Enter**.</span></span>

2. <span data-ttu-id="a4a8e-115">Installez les [Kit SDK .net Core](https://dotnet.microsoft.com/download) et [Visual Studio code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="a4a8e-115">Install the [.NET Core SDK](https://dotnet.microsoft.com/download) and [Visual Studio Code](https://code.visualstudio.com).</span></span>

3. <span data-ttu-id="a4a8e-116">Sélectionnez l’icône extensions et recherchez « Ionide » :</span><span class="sxs-lookup"><span data-stu-id="a4a8e-116">Select the Extensions icon and search for "Ionide":</span></span>

   <span data-ttu-id="a4a8e-117">Le seul plug-in F# requis pour la prise en charge de Visual Studio code est [Ionide-FSharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="a4a8e-117">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="a4a8e-118">Toutefois, vous pouvez également installer [Ionide-factice](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) pour avoir une prise en charge [factice](https://fake.build/) et [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) pour bénéficier de la prise en charge d' [Paket](https://fsprojects.github.io/Paket/) .</span><span class="sxs-lookup"><span data-stu-id="a4a8e-118">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="a4a8e-119">FACTICE et Paket sont des F# outils de la communauté supplémentaires pour la génération de projets et la gestion des dépendances, respectivement.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-119">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="a4a8e-120">Installer F# avec Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="a4a8e-120">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="a4a8e-121">F#est installé par défaut dans [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), quelle que soit la configuration choisie.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-121">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="a4a8e-122">Une fois l’installation terminée, choisissez **démarrer Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-122">After the install completes, choose **Start Visual Studio**.</span></span> <span data-ttu-id="a4a8e-123">Vous pouvez également ouvrir Visual Studio à l’aide de la recherche sur macOS.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-123">You can also open Visual Studio through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="a4a8e-124">Installer F# sur un serveur de builds</span><span class="sxs-lookup"><span data-stu-id="a4a8e-124">Install F# on a build server</span></span>

<span data-ttu-id="a4a8e-125">Si vous utilisez .NET Core ou .NET Framework via le kit de développement logiciel (SDK) .NET, il vous suffit d’installer le kit de développement logiciel (SDK) .NET sur votre serveur de builds.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-125">If you're using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="a4a8e-126">C’est tout ce dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-126">It has everything you need.</span></span>

<span data-ttu-id="a4a8e-127">Si vous utilisez .NET Framework et que vous n’utilisez **pas** le kit de développement logiciel (SDK) .net, vous devez installer la [référence SKU Visual Studio Build Tools](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) sur votre serveur Windows.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-127">If you're using .NET Framework and you are **not** using the .NET SDK, then you'll need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="a4a8e-128">Dans le programme d’installation, sélectionnez **outils de génération de bureaux .net**, puis sélectionnez le  **F# composant compilateur** sur le côté droit du menu installer.</span><span class="sxs-lookup"><span data-stu-id="a4a8e-128">In the installer, select **.NET desktop build tools**, and then select the **F# compiler** component on the right-hand side of the installer menu.</span></span>
