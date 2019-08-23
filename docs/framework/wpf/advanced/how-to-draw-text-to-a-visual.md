---
title: 'Procédure : Ajouter du texte à un visuel'
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
ms.openlocfilehash: bd760a06150098d0fff17dbdce95b55a0e5fe713
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963851"
---
# <a name="how-to-draw-text-to-a-visual"></a><span data-ttu-id="2ad01-102">Procédure : Ajouter du texte à un visuel</span><span class="sxs-lookup"><span data-stu-id="2ad01-102">How to: Draw Text to a Visual</span></span>
<span data-ttu-id="2ad01-103">L’exemple suivant montre comment dessiner du texte à <xref:System.Windows.Media.DrawingVisual> l’aide d’un <xref:System.Windows.Media.DrawingContext> objet.</span><span class="sxs-lookup"><span data-stu-id="2ad01-103">The following example shows how to draw text to a <xref:System.Windows.Media.DrawingVisual> using a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="2ad01-104">Un contexte de dessin est retourné en appelant <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> la méthode d' <xref:System.Windows.Media.DrawingVisual> un objet.</span><span class="sxs-lookup"><span data-stu-id="2ad01-104">A drawing context is returned by calling the <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> method of a <xref:System.Windows.Media.DrawingVisual> object.</span></span> <span data-ttu-id="2ad01-105">Vous pouvez dessiner des graphiques et du texte dans un contexte de dessin.</span><span class="sxs-lookup"><span data-stu-id="2ad01-105">You can draw graphics and text into a drawing context.</span></span>  
  
 <span data-ttu-id="2ad01-106">Pour dessiner du texte dans le contexte de dessin, <xref:System.Windows.Media.DrawingContext.DrawText%2A> utilisez la méthode <xref:System.Windows.Media.DrawingContext> d’un objet.</span><span class="sxs-lookup"><span data-stu-id="2ad01-106">To draw text into the drawing context, use the <xref:System.Windows.Media.DrawingContext.DrawText%2A> method of a <xref:System.Windows.Media.DrawingContext> object.</span></span> <span data-ttu-id="2ad01-107">Lorsque vous avez terminé de dessiner du contenu dans le contexte de dessin <xref:System.Windows.Media.DrawingContext.Close%2A> , appelez la méthode pour fermer le contexte de dessin et rendre le contenu persistant.</span><span class="sxs-lookup"><span data-stu-id="2ad01-107">When you are finished drawing content into the drawing context, call the <xref:System.Windows.Media.DrawingContext.Close%2A> method to close the drawing context and persist the content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ad01-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ad01-108">Example</span></span>  
 [!code-csharp[DrawingVisualSample#110](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#110)]
 [!code-vb[DrawingVisualSample#110](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#110)]  
  
> [!NOTE]
> <span data-ttu-id="2ad01-109">Pour consulter l’intégralité de l’exemple de code duquel l’exemple de code précédent a été extrait, référez-vous à la section [Hit Test Using DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994) (Test de positionnement à l’aide d’exemples de DrawingVisuals).</span><span class="sxs-lookup"><span data-stu-id="2ad01-109">For the complete code sample from which the preceding code example was extracted, see [Hit Test Using DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994).</span></span>
