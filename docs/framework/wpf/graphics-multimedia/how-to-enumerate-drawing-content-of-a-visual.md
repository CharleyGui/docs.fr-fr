---
title: 'Procédure : Énumérer le contenu de dessin d’un visuel'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 25aa0c3706005c1e16cedd7e06914db764545ebb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930067"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a><span data-ttu-id="b48a0-102">Procédure : Énumérer le contenu de dessin d’un visuel</span><span class="sxs-lookup"><span data-stu-id="b48a0-102">How to: Enumerate Drawing Content of a Visual</span></span>
<span data-ttu-id="b48a0-103">L' <xref:System.Windows.Media.Drawing> objet fournit un modèle objet pour énumérer le contenu d’un <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="b48a0-103">The <xref:System.Windows.Media.Drawing> object provide an object model for enumerating the contents of a <xref:System.Windows.Media.Visual>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b48a0-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b48a0-104">Example</span></span>  
 <span data-ttu-id="b48a0-105">L’exemple suivant utilise la <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> méthode pour récupérer la <xref:System.Windows.Media.DrawingGroup> valeur d’un <xref:System.Windows.Media.Visual> et l’énumérer.</span><span class="sxs-lookup"><span data-stu-id="b48a0-105">The following example uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method to retrieve the <xref:System.Windows.Media.DrawingGroup> value of a <xref:System.Windows.Media.Visual> and enumerate it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b48a0-106">Lorsque vous énumérez le contenu du visuel, vous récupérez <xref:System.Windows.Media.Drawing> des objets, et non la représentation sous-jacente des données de rendu sous la forme d’une liste d’instructions de graphismes vectoriels.</span><span class="sxs-lookup"><span data-stu-id="b48a0-106">When you are enumerating the contents of the visual, you are retrieving <xref:System.Windows.Media.Drawing> objects, and not the underlying representation of the render data as a vector graphics instruction list.</span></span> <span data-ttu-id="b48a0-107">Pour plus d’informations, consultez [Vue d’ensemble du rendu graphique WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b48a0-107">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a><span data-ttu-id="b48a0-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b48a0-108">See also</span></span>

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="b48a0-109">Vue d’ensemble des objets de dessin</span><span class="sxs-lookup"><span data-stu-id="b48a0-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="b48a0-110">Vue d’ensemble du rendu graphique de WPF</span><span class="sxs-lookup"><span data-stu-id="b48a0-110">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
