---
title: "Comment : mettre à l'échelle un élément"
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 34d954f68747be9eedc0ef71634e0c18b411d260
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112048"
---
# <a name="how-to-scale-an-element"></a>Comment : mettre à l'échelle un élément
Cet exemple montre comment <xref:System.Windows.Media.ScaleTransform> utiliser un élément à l’échelle.  
  
 Utilisez <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> les <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriétés et les propriétés pour resize l’élément par le facteur que vous spécifiez. Par exemple, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> une valeur de 1,5 étend l’élément à 150 pour cent de sa largeur d’origine. Une <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> valeur de 0,5 réduit la hauteur d’un élément de 50 pour cent.  
  
 Utilisez <xref:System.Windows.Media.ScaleTransform.CenterX%2A> le <xref:System.Windows.Media.ScaleTransform.CenterY%2A> et les propriétés pour spécifier le point qui est le centre de l’opération échelle. Par défaut, <xref:System.Windows.Media.ScaleTransform> a est centré au point (0,0), ce qui correspond au coin supérieur gauche du rectangle. Cela a pour effet de déplacer l’élément et aussi de <xref:System.Windows.Media.Transform>le faire paraître plus grand, parce que lorsque vous appliquez un , vous modifiez l’espace de coordonnées dans lequel l’objet réside.  
  
 L’exemple suivant <xref:System.Windows.Media.ScaleTransform> utilise un pour doubler la taille d’un 50-par-50 <xref:System.Windows.Shapes.Rectangle>. Le <xref:System.Windows.Media.ScaleTransform> a une valeur de 0 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> (la valeur) pour les deux et <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 Typiquement, vous <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A> définissez et au centre de l’objet qui est mis à l’échelle: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).  
  
 L’exemple suivant <xref:System.Windows.Shapes.Rectangle> montre un autre qui est doublé de taille; cependant, <xref:System.Windows.Media.ScaleTransform> cela a une valeur de <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>25 pour les deux et , qui correspond au centre du rectangle.  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 L’illustration suivante montre la <xref:System.Windows.Media.ScaleTransform> différence entre les deux opérations. La ligne en pointillés affiche la taille et la position du rectangle avant la mise à l’échelle.  
  
 ![Échelles de 2x avec différents points centraux](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
Deux opérations ScaleTransform avec des valeurs ScaleX et ScaleY identiques, mais des centres différents  
  
 Pour l’échantillon complet, voir [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [Vue d'ensemble des transformations](transforms-overview.md)
- [Sujets comment se passer](transformations-how-to-topics.md)
