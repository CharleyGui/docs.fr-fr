---
title: Bien démarrer avec .NET Core
description: Trouvez des ressources pour apprendre à créer des applications .NET Core sur Windows, Linux et macOS.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 0968d9db1dbfbdc8c586328ee8e02315f17950b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714396"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="64230-103">Bien démarrer avec .NET Core</span><span class="sxs-lookup"><span data-stu-id="64230-103">Get started with .NET Core</span></span>

<span data-ttu-id="64230-104">Cet article fournit des informations pour bien démarrer avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="64230-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="64230-105">.NET Core peut être installé sur Windows, Linux et macOS.</span><span class="sxs-lookup"><span data-stu-id="64230-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="64230-106">Vous pouvez coder dans l’éditeur de texte de votre choix et produire des bibliothèques et des applications multiplateformes.</span><span class="sxs-lookup"><span data-stu-id="64230-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="64230-107">Si vous ne savez pas réellement à quoi sert .NET Core ou comment ce produit s’articule avec les autres technologies .NET, commencez par consulter l’article de présentation [Qu’est-ce que .NET ?](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet).</span><span class="sxs-lookup"><span data-stu-id="64230-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="64230-108">Pour schématiser, .NET Core est une implémentation open source multiplateforme de .NET.</span><span class="sxs-lookup"><span data-stu-id="64230-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="64230-109">Créer une application</span><span class="sxs-lookup"><span data-stu-id="64230-109">Create an application</span></span>

<span data-ttu-id="64230-110">Tout d’abord, téléchargez et installez le [kit SDK .NET Core](https://dotnet.microsoft.com/download) sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="64230-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="64230-111">Ensuite, ouvrez un terminal tel que **PowerShell**, une **invite de commandes** ou **Bash**.</span><span class="sxs-lookup"><span data-stu-id="64230-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="64230-112">Tapez `dotnet` les commandes suivantes pour créer et exécuter une application CMD :</span><span class="sxs-lookup"><span data-stu-id="64230-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="64230-113">Vous devez normalement voir la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="64230-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="64230-114">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="64230-114">Congratulations!</span></span> <span data-ttu-id="64230-115">Vous avez créé une application .NET Core simple.</span><span class="sxs-lookup"><span data-stu-id="64230-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="64230-116">Vous pouvez aussi utiliser [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows uniquement) ou [Visual Studio pour Mac](./tutorials/using-on-mac-vs.md) (macOS uniquement) pour créer une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="64230-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](./tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="64230-117">Tutoriels</span><span class="sxs-lookup"><span data-stu-id="64230-117">Tutorials</span></span>

<span data-ttu-id="64230-118">Commencer à développer des applications .NET Core en suivant ces tutoriels étape par étape:</span><span class="sxs-lookup"><span data-stu-id="64230-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="64230-119">Windows</span><span class="sxs-lookup"><span data-stu-id="64230-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="64230-120">Créez votre première application console .NET Core dans Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="64230-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="64230-121">Construire une bibliothèque de classe avec .NET Standard en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="64230-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="64230-122">Démarrer avec .NET Core en utilisant le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="64230-122">Get started with .NET Core using the .NET Core CLI</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="64230-123">![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regarder une vidéo")</span><span class="sxs-lookup"><span data-stu-id="64230-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="64230-124">Regardez comment [installer et utiliser Visual Studio Code et .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) vidéo sur Channel 9.</span><span class="sxs-lookup"><span data-stu-id="64230-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="64230-125">![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regarder une vidéo")</span><span class="sxs-lookup"><span data-stu-id="64230-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="64230-126">Regardez les vidéos [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) sur YouTube.</span><span class="sxs-lookup"><span data-stu-id="64230-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="64230-127">Consultez l’article [.NET Core sur les dépendances et les exigences pour](install/dependencies.md?pivots=os-windows) une liste des versions Windows prises en charge.</span><span class="sxs-lookup"><span data-stu-id="64230-127">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linux"></a>[<span data-ttu-id="64230-128">Linux</span><span class="sxs-lookup"><span data-stu-id="64230-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="64230-129">Commencer à développer des applications .NET Core en suivant ces tutoriels étape par étape:</span><span class="sxs-lookup"><span data-stu-id="64230-129">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="64230-130">Démarrer avec .NET Core en utilisant la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="64230-130">Get started with .NET Core using the command line</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="64230-131">![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regarder une vidéo")</span><span class="sxs-lookup"><span data-stu-id="64230-131">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="64230-132">Visionnez une vidéo qui explique comment [bien démarrer avec Visual Studio Code en utilisant C# et .NET Core sur Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="64230-132">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="64230-133">Voir l’article [.NET Core dépendances et exigences](install/dependencies.md?pivots=os-linux) pour une liste des distros linux pris en charge et les versions.</span><span class="sxs-lookup"><span data-stu-id="64230-133">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macos"></a>[<span data-ttu-id="64230-134">macOS</span><span class="sxs-lookup"><span data-stu-id="64230-134">macOS</span></span>](#tab/macos)

<span data-ttu-id="64230-135">Commencer à développer des applications .NET Core en suivant ces tutoriels étape par étape:</span><span class="sxs-lookup"><span data-stu-id="64230-135">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="64230-136">Bien démarrer avec .NET Core sur macOS en utilisant Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="64230-136">Get started with .NET Core on macOS using Visual Studio Code</span></span>](./tutorials/using-on-macos.md)
- [<span data-ttu-id="64230-137">Démarrer avec .NET Core en utilisant la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="64230-137">Get started with .NET Core using the command-line</span></span>](./tutorials/cli-create-console-app.md)
- [<span data-ttu-id="64230-138">Bien démarrer avec .NET Core sur macOS à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="64230-138">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="64230-139">Construire une solution complète .NET Core sur macOS à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="64230-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| <span data-ttu-id="64230-140">![Icône représentant une caméra pour les vidéos](media/video-icon.png "Regarder une vidéo")</span><span class="sxs-lookup"><span data-stu-id="64230-140">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="64230-141">Regardez une vidéo sur [le démarrage avec Visual Studio Code à l’aide de C et .NET Core sur macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="64230-141">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="64230-142">Voir l’article [.NET Core dépendances et exigences](install/dependencies.md?pivots=os-macos) pour une liste des versions OS X / macOS prises en charge.</span><span class="sxs-lookup"><span data-stu-id="64230-142">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
