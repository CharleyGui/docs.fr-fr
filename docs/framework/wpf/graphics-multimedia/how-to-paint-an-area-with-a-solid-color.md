---
title: 'Comment : peindre une zone avec une couleur unie'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: be28a0af04c4e43cdf745a5429468aee99e34c40
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849520"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a><span data-ttu-id="894bc-102">Comment : peindre une zone avec une couleur unie</span><span class="sxs-lookup"><span data-stu-id="894bc-102">How to: Paint an Area with a Solid Color</span></span>
<span data-ttu-id="894bc-103">Pour peindre une zone avec une couleur solide, vous pouvez utiliser <xref:System.Windows.Media.Brushes.Red%2A> <xref:System.Windows.Media.Brushes.Blue%2A>un pinceau système prédéfini, tel que ou, ou vous pouvez créer un nouveau <xref:System.Windows.Media.SolidColorBrush> et décrire son <xref:System.Windows.Media.SolidColorBrush.Color%2A> utilisation alpha, rouge, vert, et les valeurs bleues.</span><span class="sxs-lookup"><span data-stu-id="894bc-103">To paint an area with a solid color, you can use a predefined system brush, such as <xref:System.Windows.Media.Brushes.Red%2A> or <xref:System.Windows.Media.Brushes.Blue%2A>, or you can create a new <xref:System.Windows.Media.SolidColorBrush> and describe its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using alpha, red, green, and blue values.</span></span> <span data-ttu-id="894bc-104">En XAML, vous pouvez également peindre une zone avec une couleur unie à l’aide de la notation hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="894bc-104">In XAML, you may also paint an area with a solid color by using hexidecimal notation.</span></span>  
  
 <span data-ttu-id="894bc-105">Les exemples suivants utilisent chacune <xref:System.Windows.Shapes.Rectangle> de ces techniques pour peindre un bleu.</span><span class="sxs-lookup"><span data-stu-id="894bc-105">The following examples uses each of these techniques to paint a <xref:System.Windows.Shapes.Rectangle> blue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="894bc-106"> Exemple</span><span class="sxs-lookup"><span data-stu-id="894bc-106">Example</span></span>  
 <span data-ttu-id="894bc-107">**Utilisation d’un pinceau prédéfini**</span><span class="sxs-lookup"><span data-stu-id="894bc-107">**Using a Predefined Brush**</span></span>  
  
 <span data-ttu-id="894bc-108">Dans l’exemple suivant utilise le <xref:System.Windows.Media.Brushes.Blue%2A> pinceau prédéfini pour peindre un rectangle bleu.</span><span class="sxs-lookup"><span data-stu-id="894bc-108">In the following example uses the predefined brush <xref:System.Windows.Media.Brushes.Blue%2A> to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 <span data-ttu-id="894bc-109">**Utilisation de la notation hexadécimale**</span><span class="sxs-lookup"><span data-stu-id="894bc-109">**Using Hexadecimal Notation**</span></span>  
  
 <span data-ttu-id="894bc-110">L’exemple suivant utilise une notation hexadécimale à 8 chiffres pour peindre un rectangle en bleu.</span><span class="sxs-lookup"><span data-stu-id="894bc-110">The next example uses 8-digit hexadecimal notation to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 <span data-ttu-id="894bc-111">**Utilisation de valeurs ARGB**</span><span class="sxs-lookup"><span data-stu-id="894bc-111">**Using ARGB Values**</span></span>  
  
 <span data-ttu-id="894bc-112">L’exemple suivant <xref:System.Windows.Media.SolidColorBrush> crée un <xref:System.Windows.Media.SolidColorBrush.Color%2A> et décrit son utilisation des valeurs ARGB pour la couleur bleue.</span><span class="sxs-lookup"><span data-stu-id="894bc-112">The next example creates a <xref:System.Windows.Media.SolidColorBrush> and describes its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using the ARGB values for the color blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 <span data-ttu-id="894bc-113">Pour d’autres façons de <xref:System.Windows.Media.Color> décrire la couleur, voir la structure.</span><span class="sxs-lookup"><span data-stu-id="894bc-113">For other ways of describing color, see the <xref:System.Windows.Media.Color> structure.</span></span>  
  
 <span data-ttu-id="894bc-114">**Sujets connexes**</span><span class="sxs-lookup"><span data-stu-id="894bc-114">**Related Topics**</span></span>  
  
 <span data-ttu-id="894bc-115">Pour plus <xref:System.Windows.Media.SolidColorBrush> d’informations et d’autres exemples, consultez la vue d’ensemble [de Painting with Solid Colors and Gradients Overview.](painting-with-solid-colors-and-gradients-overview.md)</span><span class="sxs-lookup"><span data-stu-id="894bc-115">For more information about <xref:System.Windows.Media.SolidColorBrush> and additional examples, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md) overview.</span></span>  
  
 <span data-ttu-id="894bc-116">Cet exemple de code fait partie <xref:System.Windows.Media.SolidColorBrush> d’un exemple plus large fourni pour la classe.</span><span class="sxs-lookup"><span data-stu-id="894bc-116">This code example is part of a larger example provided for the <xref:System.Windows.Media.SolidColorBrush> class.</span></span> <span data-ttu-id="894bc-117">Pour l’exemple complet, consultez [Exemples de pinceaux](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="894bc-117">For the complete sample, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894bc-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="894bc-118">See also</span></span>

- <xref:System.Windows.Media.Brushes>
