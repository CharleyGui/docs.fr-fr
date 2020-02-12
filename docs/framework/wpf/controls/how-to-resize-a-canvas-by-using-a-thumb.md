---
title: "Comment : redimensionner un Canvas à l'aide d'un curseur"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resizing Canvas control [WPF]
- controls [WPF], Thumb
- controls [WPF], Canvas
- Thumb control [WPF]
- Canvas control [WPF]
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
ms.openlocfilehash: 84f5ac2b53124b7f4d7c15741e94b40e7ee81526
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124297"
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a><span data-ttu-id="e59a9-102">Comment : redimensionner un Canvas à l'aide d'un curseur</span><span class="sxs-lookup"><span data-stu-id="e59a9-102">How to: Resize a Canvas by Using a Thumb</span></span>
<span data-ttu-id="e59a9-103">Cet exemple montre comment utiliser un contrôle <xref:System.Windows.Controls.Primitives.Thumb> pour redimensionner un contrôle <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="e59a9-103">This example shows how to use a <xref:System.Windows.Controls.Primitives.Thumb> control to resize a <xref:System.Windows.Controls.Canvas> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e59a9-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e59a9-104">Example</span></span>  
 <span data-ttu-id="e59a9-105">Le contrôle <xref:System.Windows.Controls.Primitives.Thumb> fournit des fonctionnalités de glissement qui peuvent être utilisées pour déplacer ou redimensionner des contrôles en surveillant les événements <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> et <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> de l' <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="e59a9-105">The <xref:System.Windows.Controls.Primitives.Thumb> control provides drag functionality that can be used to move or resize controls by monitoring the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>, <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> events of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="e59a9-106">L’utilisateur commence une opération glisser en appuyant sur le bouton gauche de la souris lorsque le pointeur de la souris est suspendu sur le contrôle de <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="e59a9-106">The user begins a drag operation by pressing the left mouse button when the mouse pointer is paused on the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="e59a9-107">L’opération glisser se poursuit aussi longtemps que le bouton gauche de la souris reste enfoncé.</span><span class="sxs-lookup"><span data-stu-id="e59a9-107">The drag operation continues as long as the left mouse button remains pressed.</span></span> <span data-ttu-id="e59a9-108">Au cours de l’opération glisser, l' <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> peut se produire plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="e59a9-108">During the drag operation, the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> can occur more than once.</span></span> <span data-ttu-id="e59a9-109">À chaque fois qu’il se produit, la classe <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> fournit la modification de position qui correspond à la modification de la position de la souris.</span><span class="sxs-lookup"><span data-stu-id="e59a9-109">Each time it occurs, the <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> class provides the change in position that corresponds to the change in mouse position.</span></span> <span data-ttu-id="e59a9-110">Lorsque l’utilisateur relâche le bouton gauche de la souris, l’opération glisser est terminée.</span><span class="sxs-lookup"><span data-stu-id="e59a9-110">When the user releases the left mouse button, the drag operation is finished.</span></span> <span data-ttu-id="e59a9-111">L’opération glisser fournit uniquement de nouvelles coordonnées ; elle ne repositionne pas automatiquement le <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="e59a9-111">The drag operation only provides new coordinates; it does not automatically reposition the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 <span data-ttu-id="e59a9-112">L’exemple suivant montre un contrôle <xref:System.Windows.Controls.Primitives.Thumb> qui est l’élément enfant d’un contrôle <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="e59a9-112">The following example shows a <xref:System.Windows.Controls.Primitives.Thumb> control that is the child element of a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="e59a9-113">Le gestionnaire d’événements pour son événement <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> fournit la logique pour déplacer le <xref:System.Windows.Controls.Primitives.Thumb> et redimensionner le <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="e59a9-113">The event handler for its <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event provides the logic to move the <xref:System.Windows.Controls.Primitives.Thumb> and resize the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="e59a9-114">Les gestionnaires d’événements pour l’événement <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> et <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> changent la couleur de la <xref:System.Windows.Controls.Primitives.Thumb> pendant une opération glisser.</span><span class="sxs-lookup"><span data-stu-id="e59a9-114">The event handlers for the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> and <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event change the color of the <xref:System.Windows.Controls.Primitives.Thumb> during a drag operation.</span></span> <span data-ttu-id="e59a9-115">L’exemple suivant définit le <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="e59a9-115">The following example defines the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
 [!code-xaml[Thumb#thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 <span data-ttu-id="e59a9-116">L’exemple suivant montre le gestionnaire d’événements <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> qui déplace le <xref:System.Windows.Controls.Primitives.Thumb> et redimensionne le <xref:System.Windows.Controls.Canvas> en réponse à un mouvement de la souris.</span><span class="sxs-lookup"><span data-stu-id="e59a9-116">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> event handler that moves the <xref:System.Windows.Controls.Primitives.Thumb> and resizes the <xref:System.Windows.Controls.Canvas> in response to a mouse movement.</span></span>  
  
 [!code-csharp[Thumb#2](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 <span data-ttu-id="e59a9-117">L’exemple suivant montre le gestionnaire d’événements <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>.</span><span class="sxs-lookup"><span data-stu-id="e59a9-117">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragStartedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 <span data-ttu-id="e59a9-118">L’exemple suivant montre le gestionnaire d’événements <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>.</span><span class="sxs-lookup"><span data-stu-id="e59a9-118">The following example shows the <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> event handler.</span></span>  
  
 [!code-csharp[Thumb#DragCompletedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 <span data-ttu-id="e59a9-119">Pour obtenir l’exemple complet, consultez [exemple de fonctionnalités Thumb Drag](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).</span><span class="sxs-lookup"><span data-stu-id="e59a9-119">For the complete sample, see [Thumb Drag Functionality Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Drag%20and%20Drop/DragDropThumbOps).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e59a9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e59a9-120">See also</span></span>

- <xref:System.Windows.Controls.Primitives.Thumb>
- <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>
- <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>
- <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
