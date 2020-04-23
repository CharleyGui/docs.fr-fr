---
title: Outils pour les développeurs Azure .NET et .NET Core
description: Obtenez les outils pour commencer à utiliser les bibliothèques .NET Azure à partir d’un environnement Windows, Linux et Mac.
ms.date: 10/01/2018
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: 1c6370e4b3e5e6e901ba6ef56c65d794f3da5abe
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071940"
---
# <a name="tools-for-net-and-net-core-azure-developers"></a><span data-ttu-id="79f83-103">Outils pour les développeurs Azure .NET et .NET Core</span><span class="sxs-lookup"><span data-stu-id="79f83-103">Tools for .NET and .NET Core Azure developers</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="79f83-104">Téléchargements SDK</span><span class="sxs-lookup"><span data-stu-id="79f83-104">SDK downloads</span></span>

<span data-ttu-id="79f83-105">Les bibliothèques Azure pour .NET sont mises en œuvre sous forme [de forfaits NuGet](https://www.nuget.org/packages?q=windowsazureofficial).</span><span class="sxs-lookup"><span data-stu-id="79f83-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="79f83-106">Voir la [référence API](/dotnet/api/overview/azure/?view=azure-dotnet) pour les instructions d’installation organisées par le service Azure.</span><span class="sxs-lookup"><span data-stu-id="79f83-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for installation instructions organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="79f83-107">Outils de développement</span><span class="sxs-lookup"><span data-stu-id="79f83-107">Development tools</span></span>

<span data-ttu-id="79f83-108">Visual Studio dispose d’outillage pour de nombreux services Azure intégré.</span><span class="sxs-lookup"><span data-stu-id="79f83-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="79f83-109">Certains services Azure disposent d’outils ou d’émulateurs supplémentaires, comme [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span><span class="sxs-lookup"><span data-stu-id="79f83-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="79f83-110">Consultez la documentation de votre service Azure pour tout outil supplémentaire, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="79f83-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="79f83-111">Ces instructions installent l’environnement de développement de démarrage recommandé pour votre système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="79f83-111">These instructions install the recommended starting development environment for your operating system.</span></span>

## <a name="windows"></a>[<span data-ttu-id="79f83-112">Windows</span><span class="sxs-lookup"><span data-stu-id="79f83-112">Windows</span></span>](#tab/windows)

<span data-ttu-id="79f83-113">Visual Studio versions 2017 et plus tard ont intégré dans le soutien pour le développement Azure.</span><span class="sxs-lookup"><span data-stu-id="79f83-113">Visual Studio versions 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="79f83-114">Les étapes ci-dessous décrivent l’activation du support de développement Azure dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79f83-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="79f83-115">Pour Visual Studio 2015 et plus tôt, <a href="vs2015-install.md">suivez ces instructions</a>.</span><span class="sxs-lookup"><span data-stu-id="79f83-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="79f83-116">Étape 1: Télécharger Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="79f83-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="79f83-117">Vous pouvez sauter cette étape si vous avez déjà Visual Studio 2019 installé.</span><span class="sxs-lookup"><span data-stu-id="79f83-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="79f83-118">Télécharger Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="79f83-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="79f83-119">Étape 2 : Installer les deux charges de travail Azure</span><span class="sxs-lookup"><span data-stu-id="79f83-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="79f83-120">Dans l’installateur Visual Studio, installez Visual Studio (ou modifiez une installation existante).</span><span class="sxs-lookup"><span data-stu-id="79f83-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="79f83-121">Assurez-vous que les charges de travail de développement et *de ASP.NET et de développement Web* d’Azure sont sélectionnées. *Azure development*</span><span class="sxs-lookup"><span data-stu-id="79f83-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="79f83-122">Étape 3 : Développer avec .NET sur Azure</span><span class="sxs-lookup"><span data-stu-id="79f83-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="79f83-123">Commencez par [déployer votre première application web ASP.NET Core sur Azure App Service](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).</span><span class="sxs-lookup"><span data-stu-id="79f83-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="macos"></a>[<span data-ttu-id="79f83-124">macOS</span><span class="sxs-lookup"><span data-stu-id="79f83-124">macOS</span></span>](#tab/macos)

<span data-ttu-id="79f83-125">Visual Studio pour Mac contient tout ce dont vous avez besoin pour le développement Azure.</span><span class="sxs-lookup"><span data-stu-id="79f83-125">Visual Studio for Mac has everything you need for Azure development.</span></span>

### <a name="step-1-download-visual-studio-for-mac"></a><span data-ttu-id="79f83-126">Étape 1 : Télécharger Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="79f83-126">Step 1: Download Visual Studio for Mac</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="79f83-127">Télécharger Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="79f83-127">Download Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

<span data-ttu-id="79f83-128">Lors de l’installation, les outils Azure sont sélectionnés par défaut.</span><span class="sxs-lookup"><span data-stu-id="79f83-128">During installation, Azure tools are selected by default.</span></span>

## <a name="linux"></a>[<span data-ttu-id="79f83-129">Linux</span><span class="sxs-lookup"><span data-stu-id="79f83-129">Linux</span></span>](#tab/linux)

<span data-ttu-id="79f83-130">Visual Studio Code contient tout ce dont vous avez besoin pour le développement Azure sur Linux.</span><span class="sxs-lookup"><span data-stu-id="79f83-130">Visual Studio Code has everything you need for Azure development on Linux.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="79f83-131">Étape 1 : Télécharger le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="79f83-131">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="79f83-132">Le Kit de développement logiciel (SDK) et les outils de ligne de commande pour les applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="79f83-132">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="79f83-133">Télécharger le kit de développement logiciel (SDK) .NET Core</span><span class="sxs-lookup"><span data-stu-id="79f83-133">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="79f83-134">Étape 2 : Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="79f83-134">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="79f83-135">Modifiez et déboguez des applications .NET Core sur n’importe quel système d’exploitation : Windows, Mac et Linux.</span><span class="sxs-lookup"><span data-stu-id="79f83-135">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="79f83-136">Télécharger Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="79f83-136">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

---
