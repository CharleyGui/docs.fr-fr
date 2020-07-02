---
title: Comment ajouter un écran de démarrage
description: Découvrez comment ajouter une fenêtre de démarrage ou un écran de démarrage à une application Windows Presentation Foundation (WPF).
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 0d0cf2e2a550320650c3b4a0c257071a0403c32b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617958"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="7d01c-103">Comment : ajouter un écran de démarrage dans une application WPF</span><span class="sxs-lookup"><span data-stu-id="7d01c-103">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="7d01c-104">Cette rubrique montre comment ajouter une fenêtre de démarrage ou un *écran*de démarrage à une application Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="7d01c-104">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="7d01c-105">Pour ajouter une image existante sous la forme d’un écran de démarrage</span><span class="sxs-lookup"><span data-stu-id="7d01c-105">To add an existing image as a splash screen</span></span>

1. <span data-ttu-id="7d01c-106">Créez ou recherchez une image que vous souhaitez utiliser pour l’écran de démarrage.</span><span class="sxs-lookup"><span data-stu-id="7d01c-106">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="7d01c-107">Vous pouvez utiliser n’importe quel format d’image pris en charge par le composant WIC (Windows Imaging Component).</span><span class="sxs-lookup"><span data-stu-id="7d01c-107">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="7d01c-108">Par exemple, vous pouvez utiliser le format BMP, GIF, JPEG, PNG ou TIFF.</span><span class="sxs-lookup"><span data-stu-id="7d01c-108">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2. <span data-ttu-id="7d01c-109">Ajoutez le fichier image au projet d’application WPF.</span><span class="sxs-lookup"><span data-stu-id="7d01c-109">Add the image file to the WPF Application project.</span></span>

3. <span data-ttu-id="7d01c-110">Dans **Explorateur de solutions**, sélectionnez l’image.</span><span class="sxs-lookup"><span data-stu-id="7d01c-110">In **Solution Explorer**, select the image.</span></span>

4. <span data-ttu-id="7d01c-111">Dans la Fenêtre Propriétés, cliquez sur la flèche déroulante de la propriété **action de génération** .</span><span class="sxs-lookup"><span data-stu-id="7d01c-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5. <span data-ttu-id="7d01c-112">Sélectionnez **SplashScreen** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="7d01c-112">Select **SplashScreen** from the drop-down list.</span></span>

6. <span data-ttu-id="7d01c-113">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="7d01c-113">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="7d01c-114">L’image de l’écran de démarrage s’affiche au centre de l’écran, puis disparaît lorsque la fenêtre principale de l’application s’affiche.</span><span class="sxs-lookup"><span data-stu-id="7d01c-114">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="7d01c-115">Pour exclure l’écran de démarrage de la Build</span><span class="sxs-lookup"><span data-stu-id="7d01c-115">To exclude the splash screen from build</span></span>

1. <span data-ttu-id="7d01c-116">Dans **Explorateur de solutions**, sélectionnez l’image de l’écran de démarrage.</span><span class="sxs-lookup"><span data-stu-id="7d01c-116">In **Solution Explorer**, select the splash screen image.</span></span>

2. <span data-ttu-id="7d01c-117">Dans la fenêtre **Propriétés** , affectez à **action de génération** la valeur **aucun**.</span><span class="sxs-lookup"><span data-stu-id="7d01c-117">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="7d01c-118">Pour supprimer l’écran de démarrage d’une application</span><span class="sxs-lookup"><span data-stu-id="7d01c-118">To remove the splash screen from an application</span></span>

<span data-ttu-id="7d01c-119">Dans **Explorateur de solutions**, supprimez l’image de l’écran de démarrage.</span><span class="sxs-lookup"><span data-stu-id="7d01c-119">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d01c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d01c-120">See also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="7d01c-121">[Procédure : ajouter des éléments existants à un projet](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7d01c-121">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
