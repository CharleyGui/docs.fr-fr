---
title: 'Comment : créer une réflexion'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 8a5ed345c0aa25312bd74799264e1f66ab4554e0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452056"
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="9ef8a-102">Comment : créer une réflexion</span><span class="sxs-lookup"><span data-stu-id="9ef8a-102">How to: Create a Reflection</span></span>
<span data-ttu-id="9ef8a-103">Cet exemple montre comment utiliser un <xref:System.Windows.Media.VisualBrush> pour créer une réflexion.</span><span class="sxs-lookup"><span data-stu-id="9ef8a-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="9ef8a-104">Étant donné qu’un <xref:System.Windows.Media.VisualBrush> peut afficher un visuel existant, vous pouvez utiliser cette fonctionnalité pour produire des effets visuels intéressants, tels que des réflexions et un grossissement.</span><span class="sxs-lookup"><span data-stu-id="9ef8a-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ef8a-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ef8a-105">Example</span></span>  
 <span data-ttu-id="9ef8a-106">L’exemple suivant utilise une <xref:System.Windows.Media.VisualBrush> pour créer une réflexion d’un <xref:System.Windows.Controls.Border> qui contient plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="9ef8a-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="9ef8a-107">L’illustration suivante montre la sortie que l’exemple génère.</span><span class="sxs-lookup"><span data-stu-id="9ef8a-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="9ef8a-108">![Un objet visuel réfléchi](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="9ef8a-108">![A reflected Visual object](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="9ef8a-109">Objet Visual réfléchi</span><span class="sxs-lookup"><span data-stu-id="9ef8a-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="9ef8a-110">Pour l’exemple complet, qui contient des exemples qui montrent comment agrandir des parties de l’écran et comment créer des réflexions, consultez [exemple VisualBrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).</span><span class="sxs-lookup"><span data-stu-id="9ef8a-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef8a-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ef8a-111">See also</span></span>

- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="9ef8a-112">Peinture avec des objets d'image, de dessin et visuels</span><span class="sxs-lookup"><span data-stu-id="9ef8a-112">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
