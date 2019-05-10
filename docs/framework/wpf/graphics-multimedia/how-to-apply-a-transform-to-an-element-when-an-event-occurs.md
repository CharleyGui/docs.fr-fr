---
title: 'Procédure : Appliquer une transformation à un élément lorsqu’un événement se produit'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
ms.openlocfilehash: 8f04db274432c0e89c6839bef825976c8a2f853c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630750"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a><span data-ttu-id="655ad-102">Procédure : Appliquer une transformation à un élément lorsqu’un événement se produit</span><span class="sxs-lookup"><span data-stu-id="655ad-102">How to: Apply a Transform to an Element When an Event Occurs</span></span>
<span data-ttu-id="655ad-103">Cet exemple montre comment appliquer un <xref:System.Windows.Media.ScaleTransform> lorsqu’un événement se produit.</span><span class="sxs-lookup"><span data-stu-id="655ad-103">This example shows how to apply a <xref:System.Windows.Media.ScaleTransform> when an event occurs.</span></span> <span data-ttu-id="655ad-104">Le concept illustré ici est le même que celui que vous utilisez pour l’application d’autres types de transformations.</span><span class="sxs-lookup"><span data-stu-id="655ad-104">The concept that is shown here is the same that you use for applying other types of transformations.</span></span> <span data-ttu-id="655ad-105">Pour plus d’informations sur les types de transformations disponibles, consultez le <xref:System.Windows.Media.Transform> classe ou [transforme la vue d’ensemble](transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="655ad-105">For more information about the available types of transformations, see the <xref:System.Windows.Media.Transform> class or [Transforms Overview](transforms-overview.md).</span></span>  
  
 <span data-ttu-id="655ad-106">Vous pouvez appliquer une transformation à un élément de deux façons :</span><span class="sxs-lookup"><span data-stu-id="655ad-106">You can apply a transform to an element in either of these two ways:</span></span>  
  
- <span data-ttu-id="655ad-107">Si vous le faites *pas* voulez que la transformation affecte la disposition, utilisez le <xref:System.Windows.UIElement.RenderTransform%2A> propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="655ad-107">If you do *not* want the transform to affect layout, use the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
- <span data-ttu-id="655ad-108">Si vous ne souhaitez pas que la transformation affecte la disposition, utilisez le <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="655ad-108">If you do want the transform to affect layout, use the <xref:System.Windows.FrameworkElement.LayoutTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="655ad-109">L’exemple suivant applique un <xref:System.Windows.Media.ScaleTransform> à la <xref:System.Windows.UIElement.RenderTransform%2A> propriété d’un bouton.</span><span class="sxs-lookup"><span data-stu-id="655ad-109">The following example applies a <xref:System.Windows.Media.ScaleTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a button.</span></span> <span data-ttu-id="655ad-110">Lorsque la souris se déplace sur le bouton, le <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriétés de la <xref:System.Windows.Media.ScaleTransform> sont définies sur `2`, ce qui entraîne le bouton plus grand.</span><span class="sxs-lookup"><span data-stu-id="655ad-110">When the mouse moves over the button, the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties of the <xref:System.Windows.Media.ScaleTransform> are set to `2`, which causes the button to become larger.</span></span> <span data-ttu-id="655ad-111">Lorsque la souris se déplace hors du bouton, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> sont définies sur `1`, ce qui entraîne le bouton pour revenir à sa taille d’origine.</span><span class="sxs-lookup"><span data-stu-id="655ad-111">When the mouse moves off the button, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> are set to `1`, which causes the button to return to its original size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="655ad-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="655ad-112">Example</span></span>  
 [!code-xaml[ButtonTransform#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a><span data-ttu-id="655ad-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="655ad-113">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="655ad-114">Vue d’ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="655ad-114">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="655ad-115">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="655ad-115">How-to Topics</span></span>](transformations-how-to-topics.md)
- [<span data-ttu-id="655ad-116">Vue d’ensemble des événements routés</span><span class="sxs-lookup"><span data-stu-id="655ad-116">Routed Events Overview</span></span>](../advanced/routed-events-overview.md)
