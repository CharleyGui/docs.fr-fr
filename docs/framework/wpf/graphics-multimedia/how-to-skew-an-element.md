---
title: 'Comment : incliner un élément'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 10b00044c1c518641281e2e72cdb5a68474b5170
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112022"
---
# <a name="how-to-skew-an-element"></a>Comment : incliner un élément
Cet exemple montre comment <xref:System.Windows.Media.SkewTransform> utiliser un élément pour biaiser. Une inclinaison est une transformation qui étire l’espace de coordonnées de façon non uniforme. Une utilisation typique <xref:System.Windows.Media.SkewTransform> d’un est pour simuler la profondeur 3D dans des objets 2D.  
  
 Utilisez <xref:System.Windows.Media.SkewTransform.CenterX%2A> le <xref:System.Windows.Media.SkewTransform.CenterY%2A> et les propriétés <xref:System.Windows.Media.SkewTransform>pour spécifier le point central de la .  
  
 Utilisez <xref:System.Windows.Media.SkewTransform.AngleX%2A> l’angle et <xref:System.Windows.Media.SkewTransform.AngleY%2A> les propriétés pour spécifier l’angle de biais de l’axe x et de l’axe y, et pour fausser le système de coordonnées actuel le long de ces axes.  
  
 Pour prédire l’effet d’une <xref:System.Windows.Media.SkewTransform.AngleX%2A> transformation biaisée, considérez que les valeurs x-axe biaisées par rapport au système de coordonnées d’origine. Par conséquent, <xref:System.Windows.Media.SkewTransform.AngleX%2A> pour un de 30, l’axe y tourne de 30 degrés à travers l’origine et fausse les valeurs en x- par 30 degrés de cette origine. De même, un <xref:System.Windows.Media.SkewTransform.AngleY%2A> de 30 biaise les valeurs y de la forme de 30 degrés de l’origine. Notez que l’effet produit est différent de celui obtenu lorsque l’on déplace le système de coordonnées de 30 degrés sur l’axe des x ou l’axe des y.  
  
 L’exemple suivant applique un biais horizontal <xref:System.Windows.Shapes.Rectangle> de 45 degrés à un point central de (0,0).  
  
## <a name="example"></a>Exemple  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 L’exemple suivant applique un biais horizontal <xref:System.Windows.Shapes.Rectangle> de 45 degrés à un point central de (25,25).  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 L’exemple suivant applique un biais vertical <xref:System.Windows.Shapes.Rectangle> de 45 degrés à un point central de (25,25).  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 L’illustration suivante montre les différentes inclinaisons utilisées dans cet exemple.  
  
 ![Exemples de SkewTransform](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
Les trois exemples SkewTransform illustrés  
  
 Pour l’échantillon complet, voir [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [Vue d'ensemble des transformations](transforms-overview.md)
- [Sujets comment se passer](transformations-how-to-topics.md)
