---
title: Installer F#
description: Learn how to install F# based on your environment.
ms.date: 09/05/2019
ms.openlocfilehash: 592a4c7763266cee68809fca84f9604d7e96b8f1
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204875"
---
# <a name="install-f"></a><span data-ttu-id="b0edd-103">Install F\#</span><span class="sxs-lookup"><span data-stu-id="b0edd-103">Install F\#</span></span>

<span data-ttu-id="b0edd-104">You can install F# in multiple ways, depending on your environment.</span><span class="sxs-lookup"><span data-stu-id="b0edd-104">You can install F# in multiple ways, depending on your environment.</span></span>

## <a name="install-f-with-visual-studio"></a><span data-ttu-id="b0edd-105">Install F# with Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b0edd-105">Install F# with Visual Studio</span></span>

<span data-ttu-id="b0edd-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) for the first time, it will first install the Visual Studio installer.</span><span class="sxs-lookup"><span data-stu-id="b0edd-106">If you're downloading [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) for the first time, it will first install the Visual Studio installer.</span></span> <span data-ttu-id="b0edd-107">Install the appropriate SKU of Visual Studio from the installer.</span><span class="sxs-lookup"><span data-stu-id="b0edd-107">Install the appropriate SKU of Visual Studio from the installer.</span></span> <span data-ttu-id="b0edd-108">If you already have it installed, click **Modify**.</span><span class="sxs-lookup"><span data-stu-id="b0edd-108">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="b0edd-109">You'll next see a list of Workloads.</span><span class="sxs-lookup"><span data-stu-id="b0edd-109">You'll next see a list of Workloads.</span></span> <span data-ttu-id="b0edd-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span><span class="sxs-lookup"><span data-stu-id="b0edd-110">Select **ASP.NET and web development** which will install F# support and .NET Core support for ASP.NET Core projects.</span></span>

<span data-ttu-id="b0edd-111">Next, click **Modify** in the lower right-hand side.</span><span class="sxs-lookup"><span data-stu-id="b0edd-111">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="b0edd-112">This will install everything you have selected.</span><span class="sxs-lookup"><span data-stu-id="b0edd-112">This will install everything you have selected.</span></span> <span data-ttu-id="b0edd-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span><span class="sxs-lookup"><span data-stu-id="b0edd-113">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="install-f-with-visual-studio-code"></a><span data-ttu-id="b0edd-114">Install F# with Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b0edd-114">Install F# with Visual Studio Code</span></span>

<span data-ttu-id="b0edd-115">First, ensure you have [git installed](https://git-scm.com/download) and available on your PATH.</span><span class="sxs-lookup"><span data-stu-id="b0edd-115">First, ensure you have [git installed](https://git-scm.com/download) and available on your PATH.</span></span> <span data-ttu-id="b0edd-116">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span><span class="sxs-lookup"><span data-stu-id="b0edd-116">You can verify that it is installed correctly by typing `git --version` at a command prompt and pressing **Enter**.</span></span>

<span data-ttu-id="b0edd-117">Next, install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="b0edd-117">Next, install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="b0edd-118">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span><span class="sxs-lookup"><span data-stu-id="b0edd-118">You will then need [Visual Studio Code](https://code.visualstudio.com) installed.</span></span>

<span data-ttu-id="b0edd-119">Next, click the Extensions icon and search for "Ionide":</span><span class="sxs-lookup"><span data-stu-id="b0edd-119">Next, click the Extensions icon and search for "Ionide":</span></span>

<span data-ttu-id="b0edd-120">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span><span class="sxs-lookup"><span data-stu-id="b0edd-120">The only plugin required for F# support in Visual Studio Code is [Ionide-fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp).</span></span> <span data-ttu-id="b0edd-121">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span><span class="sxs-lookup"><span data-stu-id="b0edd-121">However, you can also install [Ionide-FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) to get [FAKE](https://fake.build/) support and [Ionide-Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) to get [Paket](https://fsprojects.github.io/Paket/) support.</span></span> <span data-ttu-id="b0edd-122">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span><span class="sxs-lookup"><span data-stu-id="b0edd-122">FAKE and Paket are additional F# community tools for building projects and managing dependencies, respectively.</span></span>

## <a name="install-f-with-visual-studio-for-mac"></a><span data-ttu-id="b0edd-123">Install F# with Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="b0edd-123">Install F# with Visual Studio for Mac</span></span>

<span data-ttu-id="b0edd-124">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span><span class="sxs-lookup"><span data-stu-id="b0edd-124">F# is installed by default in [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), no matter which configuration you choose.</span></span>

<span data-ttu-id="b0edd-125">After the install completes, choose "Start Visual Studio".</span><span class="sxs-lookup"><span data-stu-id="b0edd-125">After the install completes, choose "Start Visual Studio".</span></span> <span data-ttu-id="b0edd-126">You can also launch it through Finder on macOS.</span><span class="sxs-lookup"><span data-stu-id="b0edd-126">You can also launch it through Finder on macOS.</span></span>

## <a name="install-f-on-a-build-server"></a><span data-ttu-id="b0edd-127">Install F# on a Build Server</span><span class="sxs-lookup"><span data-stu-id="b0edd-127">Install F# on a Build Server</span></span>

<span data-ttu-id="b0edd-128">If you are using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span><span class="sxs-lookup"><span data-stu-id="b0edd-128">If you are using .NET Core or .NET Framework via the .NET SDK, you simply need to install the .NET SDK on your build server.</span></span> <span data-ttu-id="b0edd-129">It has everything you need.</span><span class="sxs-lookup"><span data-stu-id="b0edd-129">It has everything you need.</span></span>

<span data-ttu-id="b0edd-130">If you are using .NET Framework and you are **not** using the .NET SDK, then you will need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span><span class="sxs-lookup"><span data-stu-id="b0edd-130">If you are using .NET Framework and you are **not** using the .NET SDK, then you will need to install the [Visual Studio Build Tools SKU](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=BuildTools&rel=16) onto your Windows Server.</span></span> <span data-ttu-id="b0edd-131">In the installer, select **.NET desktop build tools** and then select the **F# compiler** component on the right side of the installer menu.</span><span class="sxs-lookup"><span data-stu-id="b0edd-131">In the installer, select **.NET desktop build tools** and then select the **F# compiler** component on the right side of the installer menu.</span></span>
