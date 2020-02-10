---
title: 'Comment : ajouter du texte à un Visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], drawing text to visuals
- visuals [WPF], drawing text to
- text [WPF], drawing to visuals
- drawing [WPF], text to visuals
ms.assetid: fee4003c-e8a6-46ec-babd-2c7f4231a101
ms.openlocfilehash: 654bfadb42f053b6dcf353d4423bddf281d69478
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094551"
---
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="7bea1-102">Comment : ajouter du texte à un Visual</span><span class="sxs-lookup"><span data-stu-id="7bea1-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="7bea1-103">L’exemple suivant montre comment dessiner du texte sur un <xref:System.Windows.Media.DrawingVisual> à l’aide d’un objet <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="7bea1-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="7bea1-104">Un contexte de dessin est retourné en appelant la méthode <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> d’un objet <xref:System.Windows.Media.DrawingVisual>.</span><span class="sxs-lookup"><span data-stu-id="7bea1-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="7bea1-105">Vous pouvez dessiner des graphiques et du texte dans un contexte de dessin.</span><span class="sxs-lookup"><span data-stu-id="7bea1-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="7bea1-106">Pour dessiner du texte dans le contexte de dessin, utilisez la méthode <xref:System.Windows.Media.DrawingContext.DrawText%2A> d’un objet <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="7bea1-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="7bea1-107">Lorsque vous avez terminé de dessiner du contenu dans le contexte de dessin, appelez la méthode <xref:System.Windows.Media.DrawingContext.Close%2A> pour fermer le contexte de dessin et conserver le contenu.</span><span class="sxs-lookup"><span data-stu-id="7bea1-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bea1-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="7bea1-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="7bea1-109">Pour consulter l’intégralité de l’exemple de code duquel l’exemple de code précédent a été extrait, référez-vous à la section [Hit Test Using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual) (Test de positionnement à l’aide d’exemples de DrawingVisuals).</span><span class="sxs-lookup"><span data-stu-id="7bea1-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).</span></span>
