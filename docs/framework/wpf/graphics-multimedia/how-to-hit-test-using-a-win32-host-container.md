---
title: "Comment : effectuer un test de positionnement à l'aide d'un conteneur hôte Win32"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: a86c1c36f75fa232d52731959371268a8b2593d7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452803"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="cbd10-102">Comment : effectuer un test de positionnement à l'aide d'un conteneur hôte Win32</span><span class="sxs-lookup"><span data-stu-id="cbd10-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="cbd10-103">Vous pouvez créer des objets visuels dans une fenêtre Win32 en fournissant un conteneur de fenêtre hôte pour les objets visuels.</span><span class="sxs-lookup"><span data-stu-id="cbd10-103">You can create visual objects within a Win32 window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="cbd10-104">Pour assurer la gestion des événements des objets visuels du conteneur, vous devez traiter les messages transmis à la boucle de filtre de messages du conteneur de fenêtre hôte.</span><span class="sxs-lookup"><span data-stu-id="cbd10-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="cbd10-105">Reportez-vous au [Didacticiel : Hébergement d’objets visuels dans une application Win32](tutorial-hosting-visual-objects-in-a-win32-application.md) pour plus d’informations sur la façon d’héberger des objets visuels dans une fenêtre Win32.</span><span class="sxs-lookup"><span data-stu-id="cbd10-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a Win32 window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbd10-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="cbd10-106">Example</span></span>  
 <span data-ttu-id="cbd10-107">Le code suivant montre comment configurer des gestionnaires d’événements de souris pour une fenêtre Win32 utilisée en tant que conteneur hôte pour les objets visuels.</span><span class="sxs-lookup"><span data-stu-id="cbd10-107">The following code shows how to set up mouse event handlers for a Win32 window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="cbd10-108">L’exemple suivant montre comment configurer un test de positionnement en réponse pour intercepter des événements de souris spécifiques.</span><span class="sxs-lookup"><span data-stu-id="cbd10-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="cbd10-109">L’objet <xref:System.Windows.Interop.HwndSource> présente [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] contenu dans une fenêtre Win32.</span><span class="sxs-lookup"><span data-stu-id="cbd10-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a Win32 window.</span></span> <span data-ttu-id="cbd10-110">La valeur de la propriété <xref:System.Windows.Interop.HwndSource.RootVisual%2A> de l’objet <xref:System.Windows.Interop.HwndSource> représente le nœud supérieur dans la hiérarchie de l’arborescence d’éléments visuels.</span><span class="sxs-lookup"><span data-stu-id="cbd10-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="cbd10-111">Pour obtenir l’exemple complet sur les objets de test de positionnement à l’aide d’un conteneur hôte Win32, consultez [test de positionnement avec l’exemple d’interopérabilité Win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).</span><span class="sxs-lookup"><span data-stu-id="cbd10-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbd10-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbd10-112">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="cbd10-113">Test de positionnement dans la couche visuelle</span><span class="sxs-lookup"><span data-stu-id="cbd10-113">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="cbd10-114">Didacticiel : hébergement d’objets visuels dans une application Win32</span><span class="sxs-lookup"><span data-stu-id="cbd10-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](tutorial-hosting-visual-objects-in-a-win32-application.md)
