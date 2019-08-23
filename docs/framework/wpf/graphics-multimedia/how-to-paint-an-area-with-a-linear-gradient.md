---
title: 'Procédure : Peindre une zone avec un pinceau dégradé linéaire'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 92c9ccd846dbbce043d13e6ba82b9fa8e72fa8b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916166"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>Procédure : Peindre une zone avec un pinceau dégradé linéaire
Cet exemple montre comment utiliser la <xref:System.Windows.Media.LinearGradientBrush> classe pour peindre une zone avec un dégradé linéaire. Dans l’exemple suivant, le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle> est peint avec un dégradé linéaire Diagonal qui passe du jaune au rouge et du bleu au vert citron.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 L’illustration suivante montre le dégradé créé par l’exemple précédent.  
  
 ![Dégradé linéaire Diagonal](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 Pour créer un dégradé linéaire horizontal, remplacez <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> de <xref:System.Windows.Media.LinearGradientBrush> par (0, 0.5) et (1, 0.5). Dans l’exemple suivant, un <xref:System.Windows.Shapes.Rectangle> est peint avec un dégradé linéaire horizontal.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 L’illustration suivante montre le dégradé créé par l’exemple précédent.  
  
 ![Dégradé linéaire horizontal](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 Pour créer un dégradé linéaire vertical, remplacez la <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> <xref:System.Windows.Media.LinearGradientBrush> valeur <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> de et de par (0.5, 0) et (0.5, 1). Dans l’exemple suivant, un <xref:System.Windows.Shapes.Rectangle> est peint avec un dégradé linéaire vertical.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 L’illustration suivante montre le dégradé créé par l’exemple précédent.  
  
 ![Dégradé linéaire vertical](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
> Les exemples de cette rubrique utilisent le système de coordonnées par défaut pour définir les points de départ et les points de terminaison. Le système de coordonnées par défaut est relatif à un cadre englobant: 0 indique 0 pour cent de la zone englobante, et 1 indique 100 pour cent de la zone englobante. Vous pouvez modifier ce système de coordonnées en affectant à la <xref:System.Windows.Media.GradientBrush.MappingMode%2A> propriété la valeur. <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType> Un système de coordonnées absolu n’est pas relatif à un rectangle englobant. Les valeurs sont interprétées directement dans l’espace local.  
  
 Pour obtenir des exemples supplémentaires, consultez [exemples](https://go.microsoft.com/fwlink/?LinkID=159973)de pinceaux. Pour plus d’informations sur les dégradés et d’autres types de pinceaux, consultez [vue d’ensemble de la peinture avec des couleurs unies et](painting-with-solid-colors-and-gradients-overview.md)des dégradés.
