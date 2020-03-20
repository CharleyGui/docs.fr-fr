---
title: 'Comment : traduire un élément'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: ba6bda09a4ee189cdd1a32eed8f65b32d1a9abe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187307"
---
# <a name="how-to-translate-an-element"></a><span data-ttu-id="20d06-102">Comment : traduire un élément</span><span class="sxs-lookup"><span data-stu-id="20d06-102">How to: Translate an Element</span></span>
<span data-ttu-id="20d06-103">Cet exemple montre comment traduire (déplacer) <xref:System.Windows.Media.TranslateTransform>un élément en utilisant un .</span><span class="sxs-lookup"><span data-stu-id="20d06-103">This example shows how to translate (move) an element by using a <xref:System.Windows.Media.TranslateTransform>.</span></span>  
  
 <span data-ttu-id="20d06-104">La <xref:System.Windows.Media.TranslateTransform> classe est particulièrement utile pour déplacer des éléments à l’intérieur des panneaux qui ne prennent pas en charge le positionnement absolu.</span><span class="sxs-lookup"><span data-stu-id="20d06-104">The <xref:System.Windows.Media.TranslateTransform> class is especially useful for moving elements inside panels that do not support absolute positioning.</span></span> <span data-ttu-id="20d06-105">Par exemple, en <xref:System.Windows.Media.TranslateTransform> appliquant un élément à la <xref:System.Windows.UIElement.RenderTransform%2A> propriété <xref:System.Windows.Controls.StackPanel> d’un élément, vous pouvez déplacer un élément dans un ou <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="20d06-105">For example, by applying a <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of an element, you can move an element within a <xref:System.Windows.Controls.StackPanel> or <xref:System.Windows.Controls.DockPanel>.</span></span>  
  
 <span data-ttu-id="20d06-106">Utilisez <xref:System.Windows.Media.TranslateTransform.X%2A> la propriété <xref:System.Windows.Media.TranslateTransform> de la pour spécifier la quantité, en pixels, pour déplacer l’élément le long de l’axe x.</span><span class="sxs-lookup"><span data-stu-id="20d06-106">Use the <xref:System.Windows.Media.TranslateTransform.X%2A> property of the <xref:System.Windows.Media.TranslateTransform> to specify the amount, in pixels, to move the element along the x-axis.</span></span> <span data-ttu-id="20d06-107">Utilisez <xref:System.Windows.Media.TranslateTransform.Y%2A> la propriété pour spécifier la quantité, en pixels, pour déplacer l’élément le long de l’axe y.</span><span class="sxs-lookup"><span data-stu-id="20d06-107">Use the <xref:System.Windows.Media.TranslateTransform.Y%2A> property to specify the amount, in pixels, to move the element along the y-axis.</span></span> <span data-ttu-id="20d06-108">Enfin, appliquez <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.UIElement.RenderTransform%2A> la propriété de l’élément.</span><span class="sxs-lookup"><span data-stu-id="20d06-108">Finally, apply the <xref:System.Windows.Media.TranslateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="20d06-109">L’exemple suivant <xref:System.Windows.Media.TranslateTransform> utilise un pour déplacer un élément de 50 pixels vers la droite et 50 pixels vers le bas.</span><span class="sxs-lookup"><span data-stu-id="20d06-109">The following example uses a <xref:System.Windows.Media.TranslateTransform> to move an element 50 pixels to the right and 50 pixels down.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20d06-110"> Exemple</span><span class="sxs-lookup"><span data-stu-id="20d06-110">Example</span></span>  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 <span data-ttu-id="20d06-111">Pour voir l’exemple complet, consultez la page [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms) (Exemple de transformations 2D).</span><span class="sxs-lookup"><span data-stu-id="20d06-111">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d06-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20d06-112">See also</span></span>

- [<span data-ttu-id="20d06-113">Vue d'ensemble des transformations</span><span class="sxs-lookup"><span data-stu-id="20d06-113">Transforms Overview</span></span>](transforms-overview.md)
