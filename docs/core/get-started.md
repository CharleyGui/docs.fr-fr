---
title: Bien démarrer avec .NET Core
description: Découvrez des ressources qui vous apprendront à créer des applications .NET Core sur Windows, Linux et macOS.
author: thraka
ms.author: adegeo
ms.date: 09/19/2019
ms.openlocfilehash: 78066f2904f6a874b71165e4fe1769b6b778ae41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428869"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="b2d93-103">Bien démarrer avec .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2d93-103">Get started with .NET Core</span></span>

<span data-ttu-id="b2d93-104">Cet article fournit des informations pour bien démarrer avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2d93-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="b2d93-105">.NET Core peut être installé sur Windows, Linux et macOS.</span><span class="sxs-lookup"><span data-stu-id="b2d93-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="b2d93-106">Vous pouvez coder dans l’éditeur de texte de votre choix et produire des bibliothèques et des applications multiplateformes.</span><span class="sxs-lookup"><span data-stu-id="b2d93-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span> 

<span data-ttu-id="b2d93-107">Si vous ne savez pas réellement à quoi sert .NET Core ou comment ce produit s’articule avec les autres technologies .NET, commencez par consulter l’article de présentation [Qu’est-ce que .NET ?](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet).</span><span class="sxs-lookup"><span data-stu-id="b2d93-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="b2d93-108">Pour schématiser, .NET Core est une implémentation open source multiplateforme de .NET.</span><span class="sxs-lookup"><span data-stu-id="b2d93-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="b2d93-109">Créer une application</span><span class="sxs-lookup"><span data-stu-id="b2d93-109">Create an application</span></span>

<span data-ttu-id="b2d93-110">Tout d’abord, téléchargez et installez le [kit SDK .NET Core](https://dotnet.microsoft.com/download) sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b2d93-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="b2d93-111">Ensuite, ouvrez un terminal tel que **PowerShell**, une **invite de commandes** ou **Bash**.</span><span class="sxs-lookup"><span data-stu-id="b2d93-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="b2d93-112">Tapez les commandes de `dotnet` suivantes pour créer et exécuter C# une application :</span><span class="sxs-lookup"><span data-stu-id="b2d93-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="b2d93-113">Vous devez voir la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="b2d93-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="b2d93-114">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="b2d93-114">Congratulations!</span></span> <span data-ttu-id="b2d93-115">Vous avez créé une application .NET Core simple.</span><span class="sxs-lookup"><span data-stu-id="b2d93-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="b2d93-116">Vous pouvez aussi utiliser [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (Windows uniquement) ou [Visual Studio pour Mac](tutorials/using-on-mac-vs.md) (macOS uniquement) pour créer une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2d93-116">You can also use [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="b2d93-117">Didacticiels</span><span class="sxs-lookup"><span data-stu-id="b2d93-117">Tutorials</span></span>

<span data-ttu-id="b2d93-118">Vous pouvez commencer à développer des applications .NET Core en suivant ces tutoriels pas à pas.</span><span class="sxs-lookup"><span data-stu-id="b2d93-118">You can get started developing .NET Core applications by following these step-by-step tutorials.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="b2d93-119">Windows</span><span class="sxs-lookup"><span data-stu-id="b2d93-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="b2d93-120">Générer une application C# « Hello World » avec .NET Core dans Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b2d93-120">Build a C# "Hello World" Application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="b2d93-121">Générer une bibliothèque de classes C# avec .NET Core dans Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b2d93-121">Build a C# class library with .NET Core in Visual Studio 2017.</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="b2d93-122">Générer une application Visual Basic « Hello World » avec .NET Core dans Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b2d93-122">Build a Visual Basic "Hello World" application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-with-visual-studio.md)
- [<span data-ttu-id="b2d93-123">Générer une bibliothèque de classes avec Visual Basic et .NET Core dans Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b2d93-123">Build a class library with Visual Basic and .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-library-with-visual-studio.md)  
- <span data-ttu-id="b2d93-124">Visionnez une vidéo qui indique [comment installer et utiliser Visual Studio Code et .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span><span class="sxs-lookup"><span data-stu-id="b2d93-124">Watch a video on [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span></span>
- <span data-ttu-id="b2d93-125">Visionnez une vidéo qui indique [comment installer et utiliser Visual Studio 2017 et .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span><span class="sxs-lookup"><span data-stu-id="b2d93-125">Watch a video on [how to install and use Visual Studio 2017 and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span></span>
- [<span data-ttu-id="b2d93-126">Bien démarrer avec .NET Core en utilisant la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b2d93-126">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)

<span data-ttu-id="b2d93-127">Pour obtenir la liste des versions de Windows prises en charge, consultez l’article sur les [dépendances et les exigences de .net Core](install/dependencies.md?tabs=netcore30&pivots=os-windows) .</span><span class="sxs-lookup"><span data-stu-id="b2d93-127">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="b2d93-128">Linux</span><span class="sxs-lookup"><span data-stu-id="b2d93-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="b2d93-129">Vous pouvez commencer à développer une application .NET Core en suivant ces didacticiels pas à pas :</span><span class="sxs-lookup"><span data-stu-id="b2d93-129">You can get started developing .NET Core application by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="b2d93-130">Bien démarrer avec .NET Core en utilisant la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b2d93-130">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)
- <span data-ttu-id="b2d93-131">Visionnez une vidéo qui explique comment [bien démarrer avec Visual Studio Code en utilisant C# et .NET Core sur Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="b2d93-131">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

<span data-ttu-id="b2d93-132">Pour obtenir la liste des versions et distributions Linux prises en charge, consultez l’article [dépendances et exigences de .net Core](install/dependencies.md?tabs=netcore30&pivots=os-linux) .</span><span class="sxs-lookup"><span data-stu-id="b2d93-132">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="b2d93-133">macOS</span><span class="sxs-lookup"><span data-stu-id="b2d93-133">macOS</span></span>](#tab/macos)

<span data-ttu-id="b2d93-134">Vous pouvez commencer à développer une application .NET Core en suivant ces didacticiels pas à pas :</span><span class="sxs-lookup"><span data-stu-id="b2d93-134">You can get started developing .NET Core application by following these step-by-step tutorials:</span></span>

- <span data-ttu-id="b2d93-135">Visionnez une vidéo qui explique comment [bien démarrer avec Visual Studio Code en utilisant C# et .NET Core sur macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="b2d93-135">Watch a video on [Getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span>
- [<span data-ttu-id="b2d93-136">Bien démarrer avec .NET Core sur macOS en utilisant Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="b2d93-136">Getting started with .NET Core on macOS, using Visual Studio Code.</span></span>](tutorials/using-on-macos.md)
- [<span data-ttu-id="b2d93-137">Bien démarrer avec .NET Core en utilisant la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b2d93-137">Getting started with .NET Core using the command-line.</span></span>](tutorials/using-with-xplat-cli.md)
- [<span data-ttu-id="b2d93-138">Bien démarrer avec .NET Core sur macOS en utilisant Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="b2d93-138">Getting started with .NET Core on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="b2d93-139">Générer une solution .NET Core complète sur macOS en utilisant Visual Studio pour Mac.</span><span class="sxs-lookup"><span data-stu-id="b2d93-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs-full-solution.md)

<span data-ttu-id="b2d93-140">Pour obtenir la liste des versions OS X/macOS prises en charge, consultez l’article [dépendances et exigences .net Core](install/dependencies.md?tabs=netcore30&pivots=os-macos) .</span><span class="sxs-lookup"><span data-stu-id="b2d93-140">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
