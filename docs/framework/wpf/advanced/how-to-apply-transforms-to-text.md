---
title: 'Comment : appliquer des transformations à du texte'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: 867f39e3df8493014d8601530e91310c3bbbeeb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141612"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="33377-102">Comment : appliquer des transformations à du texte</span><span class="sxs-lookup"><span data-stu-id="33377-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="33377-103">Les transformations peuvent modifier l’affichage de texte dans votre application.</span><span class="sxs-lookup"><span data-stu-id="33377-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="33377-104">Les exemples suivants utilisent différents types de transformations de <xref:System.Windows.Controls.TextBlock> rendu pour affecter l’affichage du texte dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="33377-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33377-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="33377-105">Example</span></span>  
 <span data-ttu-id="33377-106">L’exemple suivant présente un texte pivoté par rapport à un point spécifié dans le plan x-y à deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="33377-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 ![Texte pivoté à l'aide de RotateTransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 <span data-ttu-id="33377-108">L’exemple de <xref:System.Windows.Media.RotateTransform> code suivant utilise un texte de rotation.</span><span class="sxs-lookup"><span data-stu-id="33377-108">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="33377-109">Une <xref:System.Windows.Media.RotateTransform.Angle%2A> valeur de 90 tourne l’élément 90 degrés dans le sens des aiguilles d’une montre.</span><span class="sxs-lookup"><span data-stu-id="33377-109">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="33377-110">Dans l’exemple suivant, la deuxième ligne du texte est mise à l’échelle par 150 % le long de l’axe x et la troisième ligne du texte est mise à l’échelle par 150 % le long de l’axe y.</span><span class="sxs-lookup"><span data-stu-id="33377-110">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 ![Texte mis à l'échelle à l'aide de ScaleTransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg)
  
 <span data-ttu-id="33377-112">L’exemple de <xref:System.Windows.Media.ScaleTransform> code suivant utilise un texte à l’échelle de sa taille d’origine.</span><span class="sxs-lookup"><span data-stu-id="33377-112">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> <span data-ttu-id="33377-113">La mise à l’échelle du texte est différente de l’augmentation de la taille de police du texte.</span><span class="sxs-lookup"><span data-stu-id="33377-113">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="33377-114">Les tailles de police sont calculées indépendamment les unes des autres pour fournir la meilleure résolution à des tailles différentes.</span><span class="sxs-lookup"><span data-stu-id="33377-114">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="33377-115">Le texte mis à l’échelle, en revanche, conserve les proportions du texte à la taille d’origine.</span><span class="sxs-lookup"><span data-stu-id="33377-115">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="33377-116">L’exemple suivant présente le texte incliné le long de l’axe x.</span><span class="sxs-lookup"><span data-stu-id="33377-116">The following example shows text skewed along the x-axis.</span></span>  
  
 ![Texte incliné à l'aide de SkewTransform](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)

 <span data-ttu-id="33377-118">L’exemple de <xref:System.Windows.Media.SkewTransform> code suivant utilise un texte biaisé.</span><span class="sxs-lookup"><span data-stu-id="33377-118">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="33377-119">Une inclinaison est une transformation qui étire l’espace de coordonnées de façon non uniforme.</span><span class="sxs-lookup"><span data-stu-id="33377-119">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="33377-120">Dans cet exemple, les deux chaînes de texte sont inclinées de -30° et 30° le long de la coordonnée x.</span><span class="sxs-lookup"><span data-stu-id="33377-120">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="33377-121">L’exemple suivant présente le texte traduit ou déplacé, le long des axes x et y.</span><span class="sxs-lookup"><span data-stu-id="33377-121">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 ![Décalage de texte utilisant TranslateTransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 <span data-ttu-id="33377-123">L’exemple de <xref:System.Windows.Media.TranslateTransform> code suivant utilise un texte de compensation.</span><span class="sxs-lookup"><span data-stu-id="33377-123">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="33377-124">Dans cet exemple, une copie légèrement décalée de texte en dessous du texte principal crée un effet d’ombre.</span><span class="sxs-lookup"><span data-stu-id="33377-124">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> <span data-ttu-id="33377-125">Le <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> fournit un riche ensemble de fonctionnalités pour fournir des effets d’ombre.</span><span class="sxs-lookup"><span data-stu-id="33377-125">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="33377-126">Pour plus d’informations, voir [Créer du texte avec une ombre](how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="33377-126">For more information, see [Create Text with a Shadow](how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33377-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33377-127">See also</span></span>

- [<span data-ttu-id="33377-128">Appliquer des animations à du texte</span><span class="sxs-lookup"><span data-stu-id="33377-128">Apply Animations to Text</span></span>](how-to-apply-animations-to-text.md)
