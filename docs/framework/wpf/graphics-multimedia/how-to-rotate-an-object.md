---
title: 'Comment : faire pivoter un objet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: e17d3b7b9986b477df198480129edaf4c139c6bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112061"
---
# <a name="how-to-rotate-an-object"></a>Comment : faire pivoter un objet
Cet exemple montre comment faire pivoter un objet. L’exemple crée <xref:System.Windows.Media.RotateTransform> d’abord un, puis spécifie son <xref:System.Windows.Media.RotateTransform.Angle%2A> en degrés.  
  
 L’exemple suivant <xref:System.Windows.Shapes.Polyline> fait pivoter un objet de 45 degrés sur son coin supérieur gauche.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 Les <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriétés <xref:System.Windows.Media.RotateTransform> et les propriétés du point de rotation de l’objet. Ce point central est exprimé dans l’espace de coordonnées de l’élément transformé. Par défaut, la rotation est appliquée à (0,0), qui correspond à l’angle supérieur gauche de l’objet à transformer.  
  
 L’exemple suivant <xref:System.Windows.Shapes.Polyline> tourne un objet dans le sens des aiguilles d’une montre de 45 degrés sur le point (25,50).  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 L’illustration suivante montre les <xref:System.Windows.Media.Transform> résultats de l’application d’un sur les deux objets.  
  
 ![Rotations de 45 degrés avec différents points centraux](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
Deux objets en rotation de 45 degrés à partir de différents centres de rotation  
  
 Les <xref:System.Windows.Shapes.Polyline> exemples précédents <xref:System.Windows.UIElement>est un . Lorsque vous <xref:System.Windows.Media.Transform> appliquez <xref:System.Windows.UIElement.RenderTransform%2A> un <xref:System.Windows.UIElement>à la propriété <xref:System.Windows.UIElement.RenderTransformOrigin%2A> d’un , <xref:System.Windows.Media.Transform> vous pouvez utiliser la propriété pour spécifier une origine pour chaque que vous appliquez à l’élément. Parce <xref:System.Windows.UIElement.RenderTransformOrigin%2A> que la propriété utilise des coordonnées relatives, vous pouvez appliquer une transformation au centre de l’élément, même si vous ne connaissez pas sa taille. Pour plus d’informations et par exemple, voir [Spécifier l’origine d’une transformation en utilisant des valeurs relatives](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).  
  
 Pour l’échantillon complet, voir [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Transform>
- [Vue d'ensemble des transformations](transforms-overview.md)
- [Sujets comment se passer](transformations-how-to-topics.md)
