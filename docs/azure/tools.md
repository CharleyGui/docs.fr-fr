---
title: Outils pour les développeurs .NET d’Azure
description: Obtenez les outils pour commencer à utiliser les bibliothèques .NET Azure à partir d’un environnement Windows, Linux et Mac.
ms.date: 06/19/2020
ms.custom: azure-sdk-dotnet
ms.openlocfilehash: fa645b152f15550b25a3542ba0cdbb43799536b9
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174927"
---
# <a name="azure-tools-for-developing-with-net"></a><span data-ttu-id="bd3fa-103">Outils Azure pour le développement avec .NET</span><span class="sxs-lookup"><span data-stu-id="bd3fa-103">Azure tools for developing with .NET</span></span>

## <a name="sdk-downloads"></a><span data-ttu-id="bd3fa-104">Téléchargements du SDK</span><span class="sxs-lookup"><span data-stu-id="bd3fa-104">SDK downloads</span></span>

<span data-ttu-id="bd3fa-105">Les bibliothèques Azure pour .NET sont implémentées en tant que [packages NuGet](https://www.nuget.org/packages?q=windowsazureofficial).</span><span class="sxs-lookup"><span data-stu-id="bd3fa-105">Azure libraries for .NET are implemented as [NuGet packages](https://www.nuget.org/packages?q=windowsazureofficial).</span></span> <span data-ttu-id="bd3fa-106">Consultez les informations de référence sur l' [API](/dotnet/api/overview/azure/?view=azure-dotnet) pour la documentation de référence organisée par le service Azure.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-106">See the [API Reference](/dotnet/api/overview/azure/?view=azure-dotnet) for reference documentation organized by Azure service.</span></span>

## <a name="development-tools"></a><span data-ttu-id="bd3fa-107">Outils de développement</span><span class="sxs-lookup"><span data-stu-id="bd3fa-107">Development tools</span></span>

<span data-ttu-id="bd3fa-108">Visual Studio propose des outils pour de nombreux services Azure intégrés.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-108">Visual Studio has tooling for many Azure services built-in.</span></span> <span data-ttu-id="bd3fa-109">Certains services Azure disposent d’outils ou d’émulateurs supplémentaires, comme [Explorateur stockage Azure](https://azure.microsoft.com/features/storage-explorer/).</span><span class="sxs-lookup"><span data-stu-id="bd3fa-109">Some Azure services have additional tools or emulators available, such as [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="bd3fa-110">Consultez la documentation de votre service Azure pour obtenir des outils supplémentaires, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-110">See the documentation for your Azure service for any additional tools, if necessary.</span></span>

<span data-ttu-id="bd3fa-111">Sélectionnez votre environnement de développement par défaut ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-111">Select your preferred development environment below.</span></span>

## <a name="visual-studio-on-windows"></a>[<span data-ttu-id="bd3fa-112">Visual Studio sur Windows</span><span class="sxs-lookup"><span data-stu-id="bd3fa-112">Visual Studio on Windows</span></span>](#tab/vs)

<span data-ttu-id="bd3fa-113">Visual Studio version 2017 et versions ultérieures intègrent la prise en charge du développement Azure.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-113">Visual Studio version 2017 and later have built-in support for Azure development.</span></span> <span data-ttu-id="bd3fa-114">Les étapes ci-dessous décrivent l’activation de la prise en charge du développement Azure dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-114">The below steps describe enabling Azure development support in Visual Studio.</span></span>

<span data-ttu-id="bd3fa-115">Pour Visual Studio 2015 et versions antérieures, <a href="vs2015-install.md">suivez ces instructions</a>.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-115">For Visual Studio 2015 and earlier, <a href="vs2015-install.md">follow these instructions</a>.</span></span>

### <a name="step-1-download-visual-studio-2019"></a><span data-ttu-id="bd3fa-116">Étape 1 : Télécharger Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="bd3fa-116">Step 1: Download Visual Studio 2019</span></span>

<span data-ttu-id="bd3fa-117">Vous pouvez ignorer cette étape si vous avez déjà installé Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-117">You can skip this step if you already have Visual Studio 2019 installed.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd3fa-118">Télécharger Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="bd3fa-118">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="step-2-install-the-two-azure-workloads"></a><span data-ttu-id="bd3fa-119">Étape 2 : Installer les deux charges de travail Azure</span><span class="sxs-lookup"><span data-stu-id="bd3fa-119">Step 2: Install the two Azure workloads</span></span>

<span data-ttu-id="bd3fa-120">Dans le programme d’installation de Visual Studio, installez Visual Studio (ou modifiez une installation existante).</span><span class="sxs-lookup"><span data-stu-id="bd3fa-120">In the Visual Studio installer, install Visual Studio (or modify an existing installation).</span></span> <span data-ttu-id="bd3fa-121">Assurez-vous que les charges de travail *développement Azure* et développement *Web et ASP.net* sont sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-121">Make sure the *Azure development* and *ASP.NET and web development* workloads are selected.</span></span>

### <a name="step-3-develop-with-net-on-azure"></a><span data-ttu-id="bd3fa-122">Étape 3 : Développer avec .NET sur Azure</span><span class="sxs-lookup"><span data-stu-id="bd3fa-122">Step 3: Develop with .NET on Azure</span></span>

<span data-ttu-id="bd3fa-123">Commencez par [déployer votre première application web ASP.NET Core sur Azure App Service](/azure/app-service-web/app-service-web-get-started-dotnet).</span><span class="sxs-lookup"><span data-stu-id="bd3fa-123">Get started by [deploying your first ASP.NET Core web app on Azure App Service](/azure/app-service-web/app-service-web-get-started-dotnet).</span></span>

## <a name="visual-studio-code-cross-platform"></a>[<span data-ttu-id="bd3fa-124">Visual Studio Code (multiplateforme)</span><span class="sxs-lookup"><span data-stu-id="bd3fa-124">Visual Studio Code (cross-platform)</span></span>](#tab/vscode)

<span data-ttu-id="bd3fa-125">Visual Studio Code dispose de tout ce dont vous avez besoin pour le développement Azure multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-125">Visual Studio Code has everything you need for cross-platform Azure development.</span></span>

### <a name="step-1-download-the-net-core-sdk"></a><span data-ttu-id="bd3fa-126">Étape 1 : Télécharger le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd3fa-126">Step 1: Download the .NET Core SDK</span></span>

<span data-ttu-id="bd3fa-127">Le Kit de développement logiciel (SDK) et les outils de ligne de commande pour les applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-127">The SDK and command-line tools for .NET Core apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd3fa-128">Télécharger le kit de développement logiciel (SDK) .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd3fa-128">Download .NET Core SDK</span></span>](https://dotnet.microsoft.com/download)

### <a name="step-2-visual-studio-code"></a><span data-ttu-id="bd3fa-129">Étape 2 : Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bd3fa-129">Step 2: Visual Studio Code</span></span>

<span data-ttu-id="bd3fa-130">Modifiez et déboguez des applications .NET Core sur n’importe quel système d’exploitation : Windows, Mac et Linux.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-130">Edit and debug .NET Core apps on any operating system: Windows, Mac, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd3fa-131">Télécharger Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bd3fa-131">Download Visual Studio Code</span></span>](https://code.visualstudio.com)

### <a name="step-3-azure-tools-extension"></a><span data-ttu-id="bd3fa-132">Étape 3 : extension Azure Tools</span><span class="sxs-lookup"><span data-stu-id="bd3fa-132">Step 3: Azure Tools extension</span></span>

<span data-ttu-id="bd3fa-133">Installez l’extension Azure Tools dans Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="bd3fa-133">Install the Azure Tools extension in Visual Studio Code.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bd3fa-134">Installer l’extension Azure Tools</span><span class="sxs-lookup"><span data-stu-id="bd3fa-134">Install Azure Tools extension</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)

### <a name="step-4-develop-with-net-on-azure"></a><span data-ttu-id="bd3fa-135">Étape 4 : développer avec .NET sur Azure</span><span class="sxs-lookup"><span data-stu-id="bd3fa-135">Step 4: Develop with .NET on Azure</span></span>

<span data-ttu-id="bd3fa-136">Commencez par [déployer votre première ASP.net Core application Web sur Azure App service sur Linux](/azure/app-service/containers/quickstart-dotnetcore).</span><span class="sxs-lookup"><span data-stu-id="bd3fa-136">Get started by [deploying your first ASP.NET Core web app on Azure App Service on Linux](/azure/app-service/containers/quickstart-dotnetcore).</span></span>

---
