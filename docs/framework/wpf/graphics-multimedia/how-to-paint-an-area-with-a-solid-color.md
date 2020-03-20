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
# <a name="how-to-paint-an-area-with-a-solid-color"></a>Comment : peindre une zone avec une couleur unie
Pour peindre une zone avec une couleur solide, vous pouvez utiliser <xref:System.Windows.Media.Brushes.Red%2A> <xref:System.Windows.Media.Brushes.Blue%2A>un pinceau système prédéfini, tel que ou, ou vous pouvez créer un nouveau <xref:System.Windows.Media.SolidColorBrush> et décrire son <xref:System.Windows.Media.SolidColorBrush.Color%2A> utilisation alpha, rouge, vert, et les valeurs bleues. En XAML, vous pouvez également peindre une zone avec une couleur unie à l’aide de la notation hexadécimale.  
  
 Les exemples suivants utilisent chacune <xref:System.Windows.Shapes.Rectangle> de ces techniques pour peindre un bleu.  
  
## <a name="example"></a> Exemple  
 **Utilisation d’un pinceau prédéfini**  
  
 Dans l’exemple suivant utilise le <xref:System.Windows.Media.Brushes.Blue%2A> pinceau prédéfini pour peindre un rectangle bleu.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Utilisation de la notation hexadécimale**  
  
 L’exemple suivant utilise une notation hexadécimale à 8 chiffres pour peindre un rectangle en bleu.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **Utilisation de valeurs ARGB**  
  
 L’exemple suivant <xref:System.Windows.Media.SolidColorBrush> crée un <xref:System.Windows.Media.SolidColorBrush.Color%2A> et décrit son utilisation des valeurs ARGB pour la couleur bleue.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Pour d’autres façons de <xref:System.Windows.Media.Color> décrire la couleur, voir la structure.  
  
 **Sujets connexes**  
  
 Pour plus <xref:System.Windows.Media.SolidColorBrush> d’informations et d’autres exemples, consultez la vue d’ensemble [de Painting with Solid Colors and Gradients Overview.](painting-with-solid-colors-and-gradients-overview.md)  
  
 Cet exemple de code fait partie <xref:System.Windows.Media.SolidColorBrush> d’un exemple plus large fourni pour la classe. Pour l’exemple complet, consultez [Exemples de pinceaux](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Brushes>
