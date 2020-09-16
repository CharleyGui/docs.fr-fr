---
title: Bien démarrer avec .NET Core
description: Trouvez des ressources pour apprendre à créer des applications .NET Core sur Windows, Linux et macOS.
author: adegeo
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 6106f66dfbbe382ee9f61eb8b7bda70ab9b72d0b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538547"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="595d7-103">Bien démarrer avec .NET Core</span><span class="sxs-lookup"><span data-stu-id="595d7-103">Get started with .NET Core</span></span>

<span data-ttu-id="595d7-104">Cet article fournit des informations pour bien démarrer avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="595d7-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="595d7-105">.NET Core peut être installé sur Windows, Linux et macOS.</span><span class="sxs-lookup"><span data-stu-id="595d7-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="595d7-106">Vous pouvez coder dans l’éditeur de texte de votre choix et produire des bibliothèques et des applications multiplateformes.</span><span class="sxs-lookup"><span data-stu-id="595d7-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="595d7-107">Si vous n’êtes pas certain du .NET Core ou de son lien avec d’autres technologies .NET, commencez par la vue d’ensemble de [.net](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="595d7-107">If you're unsure what .NET Core is or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="595d7-108">Pour schématiser, .NET Core est une implémentation open source multiplateforme de .NET.</span><span class="sxs-lookup"><span data-stu-id="595d7-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="595d7-109">Créer une application</span><span class="sxs-lookup"><span data-stu-id="595d7-109">Create an application</span></span>

<span data-ttu-id="595d7-110">Tout d’abord, téléchargez et installez le [kit SDK .NET Core](https://dotnet.microsoft.com/download) sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="595d7-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="595d7-111">Ensuite, ouvrez un terminal tel que **PowerShell**, une **invite de commandes** ou **Bash**.</span><span class="sxs-lookup"><span data-stu-id="595d7-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="595d7-112">Entrez les `dotnet` commandes suivantes pour créer et exécuter une application C# :</span><span class="sxs-lookup"><span data-stu-id="595d7-112">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="595d7-113">Vous devez normalement voir la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="595d7-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="595d7-114">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="595d7-114">Congratulations!</span></span> <span data-ttu-id="595d7-115">Vous avez créé une application .NET Core simple.</span><span class="sxs-lookup"><span data-stu-id="595d7-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="595d7-116">Vous pouvez aussi utiliser [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows uniquement) ou [Visual Studio pour Mac](tutorials/with-visual-studio-mac.md) (macOS uniquement) pour créer une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="595d7-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/with-visual-studio-mac.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="595d7-117">Tutoriels</span><span class="sxs-lookup"><span data-stu-id="595d7-117">Tutorials</span></span>

<span data-ttu-id="595d7-118">Commencez à développer des applications .NET Core en suivant ces didacticiels pas à pas :</span><span class="sxs-lookup"><span data-stu-id="595d7-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="595d7-119">Windows</span><span class="sxs-lookup"><span data-stu-id="595d7-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="595d7-120">Créer votre première application de console .NET Core dans Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="595d7-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="595d7-121">Créer une bibliothèque de classes avec .NET Standard dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="595d7-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="595d7-122">Didacticiel : créer une application console .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="595d7-122">Tutorial: Create a .NET Core console app using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| <span data-ttu-id="595d7-123">![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regarder une vidéo")</span><span class="sxs-lookup"><span data-stu-id="595d7-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="595d7-124">Regardez la vidéo sur l' [installation et l’utilisation de Visual Studio code et](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) de la vidéo .net Core sur Channel 9.</span><span class="sxs-lookup"><span data-stu-id="595d7-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="595d7-125">![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regarder une vidéo")</span><span class="sxs-lookup"><span data-stu-id="595d7-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="595d7-126">Regardez les vidéos [.net Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) sur YouTube.</span><span class="sxs-lookup"><span data-stu-id="595d7-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="595d7-127">Pour obtenir la liste des versions de Windows prises en charge, consultez l’article sur les [dépendances et les exigences de .net Core](./install/windows.md) .</span><span class="sxs-lookup"><span data-stu-id="595d7-127">See the [.NET Core dependencies and requirements](./install/windows.md) article for a list of the supported Windows versions.</span></span>

# <a name="linux"></a>[<span data-ttu-id="595d7-128">Linux</span><span class="sxs-lookup"><span data-stu-id="595d7-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="595d7-129">Commencez à développer des applications .NET Core en suivant ces didacticiels pas à pas :</span><span class="sxs-lookup"><span data-stu-id="595d7-129">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="595d7-130">Didacticiel : créer une application console .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="595d7-130">Tutorial: Create a .NET Core console app using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| <span data-ttu-id="595d7-131">![Icône représentant une caméra pour les vidéos](./media/video-icon.png "Regarder une vidéo")</span><span class="sxs-lookup"><span data-stu-id="595d7-131">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="595d7-132">Visionnez une vidéo qui explique comment [bien démarrer avec Visual Studio Code en utilisant C# et .NET Core sur Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span><span class="sxs-lookup"><span data-stu-id="595d7-132">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="595d7-133">Pour obtenir la liste des versions et distributions Linux prises en charge, consultez l’article [dépendances et exigences de .net Core](./install/linux.md) .</span><span class="sxs-lookup"><span data-stu-id="595d7-133">See the [.NET Core dependencies and requirements](./install/linux.md) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macos"></a>[<span data-ttu-id="595d7-134">macOS</span><span class="sxs-lookup"><span data-stu-id="595d7-134">macOS</span></span>](#tab/macos)

<span data-ttu-id="595d7-135">Commencez à développer des applications .NET Core en suivant ces didacticiels pas à pas :</span><span class="sxs-lookup"><span data-stu-id="595d7-135">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="595d7-136">Didacticiel : créer une application console .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="595d7-136">Tutorial: Create a .NET Core console application using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)
- [<span data-ttu-id="595d7-137">Didacticiel : créer une application console .NET Core à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="595d7-137">Tutorial: Create a .NET Core console application using Visual Studio for Mac</span></span>](tutorials/with-visual-studio-mac.md)
- [<span data-ttu-id="595d7-138">Créer une bibliothèque de .NET Standard sur macOS à l’aide de Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="595d7-138">Build a .NET Standard library on macOS using Visual Studio for Mac</span></span>](tutorials/library-with-visual-studio-mac.md)

|   |   |
|---|---|
| <span data-ttu-id="595d7-139">![Icône représentant une caméra pour les vidéos](media/video-icon.png "Regarder une vidéo")</span><span class="sxs-lookup"><span data-stu-id="595d7-139">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="595d7-140">Regardez une vidéo sur la prise en main de [Visual Studio code à l’aide de C# et de .net Core sur MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span><span class="sxs-lookup"><span data-stu-id="595d7-140">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="595d7-141">Pour obtenir la liste des versions OS X/macOS prises en charge, consultez l’article [dépendances et exigences .net Core](./install/macos.md) .</span><span class="sxs-lookup"><span data-stu-id="595d7-141">See the [.NET Core dependencies and requirements](./install/macos.md) article for a list of the supported OS X / macOS versions.</span></span>

---
