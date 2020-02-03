---
title: Héberger le contenu Direct3D9 dans WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
ms.openlocfilehash: e65b0c59268b44abed289e54181bf0bda9355664
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742609"
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="aa2f7-102">Procédure pas à pas : hébergement de contenu Direct3D9 dans WPF</span><span class="sxs-lookup"><span data-stu-id="aa2f7-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>

<span data-ttu-id="aa2f7-103">Cette procédure pas à pas montre comment héberger du contenu Direct3D9 dans une application Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="aa2f7-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>

<span data-ttu-id="aa2f7-104">Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="aa2f7-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="aa2f7-105">Créez un projet WPF pour héberger le contenu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-105">Create a WPF project to host the Direct3D9 content.</span></span>

- <span data-ttu-id="aa2f7-106">Importez le contenu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-106">Import the Direct3D9 content.</span></span>

- <span data-ttu-id="aa2f7-107">Affichez le contenu Direct3D9 à l’aide de la classe <xref:System.Windows.Interop.D3DImage>.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>

 <span data-ttu-id="aa2f7-108">Quand vous aurez terminé, vous saurez comment héberger le contenu Direct3D9 dans une application WPF.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aa2f7-109">Composants requis</span><span class="sxs-lookup"><span data-stu-id="aa2f7-109">Prerequisites</span></span>

<span data-ttu-id="aa2f7-110">Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :</span><span class="sxs-lookup"><span data-stu-id="aa2f7-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="aa2f7-111">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-111">Visual Studio.</span></span>

- <span data-ttu-id="aa2f7-112">DirectX SDK 9 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-112">DirectX SDK 9 or later.</span></span>

- <span data-ttu-id="aa2f7-113">DLL qui contient le contenu Direct3D9 dans un format compatible WPF.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="aa2f7-114">Pour plus d’informations, consultez [interopérabilité WPF et Direct3D9](wpf-and-direct3d9-interoperation.md) et [procédure pas à pas : création de contenu Direct3D9 pour l’hébergement dans WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="aa2f7-114">For more information, see [WPF and Direct3D9 Interoperation](wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>

## <a name="creating-the-wpf-project"></a><span data-ttu-id="aa2f7-115">Création du projet WPF</span><span class="sxs-lookup"><span data-stu-id="aa2f7-115">Creating the WPF Project</span></span>

<span data-ttu-id="aa2f7-116">La première étape consiste à créer le projet pour l’application WPF.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-116">The first step is to create the project for the WPF application.</span></span>

### <a name="to-create-the-wpf-project"></a><span data-ttu-id="aa2f7-117">Pour créer le projet WPF</span><span class="sxs-lookup"><span data-stu-id="aa2f7-117">To create the WPF project</span></span>

<span data-ttu-id="aa2f7-118">Créez un projet d’application WPF dans Visual C# `D3DHost`.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="aa2f7-119">Pour plus d’informations, consultez [Procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="aa2f7-119">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

<span data-ttu-id="aa2f7-120">MainWindow. xaml s’ouvre dans le Concepteur WPF.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-120">MainWindow.xaml opens in the WPF Designer.</span></span>

## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="aa2f7-121">Importation du contenu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="aa2f7-121">Importing the Direct3D9 Content</span></span>

<span data-ttu-id="aa2f7-122">Vous importez le contenu Direct3D9 à partir d’une DLL non managée à l’aide de l’attribut `DllImport`.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>

### <a name="to-import-direct3d9-content"></a><span data-ttu-id="aa2f7-123">Pour importer du contenu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="aa2f7-123">To import Direct3D9 content</span></span>

1. <span data-ttu-id="aa2f7-124">Ouvrez MainWindow.xaml.cs dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>

2. <span data-ttu-id="aa2f7-125">Remplacez le code généré automatiquement par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-125">Replace the automatically generated code with the following code.</span></span>

    [!code-csharp[System.Windows.Interop.D3DImage#1](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]

## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="aa2f7-126">Hébergement du contenu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="aa2f7-126">Hosting the Direct3D9 Content</span></span>

<span data-ttu-id="aa2f7-127">Enfin, utilisez la classe <xref:System.Windows.Interop.D3DImage> pour héberger le contenu Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>

### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="aa2f7-128">Pour héberger le contenu Direct3D9</span><span class="sxs-lookup"><span data-stu-id="aa2f7-128">To host the Direct3D9 content</span></span>

1. <span data-ttu-id="aa2f7-129">Dans MainWindow. xaml, remplacez le code XAML généré automatiquement par le code XAML suivant.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>

    [!code-xaml[System.Windows.Interop.D3DImage#10](~/samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]

2. <span data-ttu-id="aa2f7-130">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="aa2f7-130">Build the project.</span></span>

3. <span data-ttu-id="aa2f7-131">Copiez la DLL qui contient le contenu Direct3D9 dans le dossier bin/debug.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>

4. <span data-ttu-id="aa2f7-132">Appuyez sur F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-132">Press F5 to run the project.</span></span>

    <span data-ttu-id="aa2f7-133">Le contenu Direct3D9 s’affiche dans l’application WPF.</span><span class="sxs-lookup"><span data-stu-id="aa2f7-133">The Direct3D9 content appears within the WPF application.</span></span>

## <a name="see-also"></a><span data-ttu-id="aa2f7-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa2f7-134">See also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="aa2f7-135">Considérations sur les performances de l'interopérabilité entre Direct3D9 et WPF</span><span class="sxs-lookup"><span data-stu-id="aa2f7-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
