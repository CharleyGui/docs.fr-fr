---
title: 'Procédure : Appliquer une transformation à un élément lorsqu’un événement se produit'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
ms.openlocfilehash: 8f04db274432c0e89c6839bef825976c8a2f853c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630750"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a>Procédure : Appliquer une transformation à un élément lorsqu’un événement se produit
Cet exemple montre comment appliquer un <xref:System.Windows.Media.ScaleTransform> lorsqu’un événement se produit. Le concept illustré ici est le même que celui que vous utilisez pour l’application d’autres types de transformations. Pour plus d’informations sur les types de transformations disponibles, consultez le <xref:System.Windows.Media.Transform> classe ou [transforme la vue d’ensemble](transforms-overview.md).  
  
 Vous pouvez appliquer une transformation à un élément de deux façons :  
  
- Si vous le faites *pas* voulez que la transformation affecte la disposition, utilisez le <xref:System.Windows.UIElement.RenderTransform%2A> propriété de l’élément.  
  
- Si vous ne souhaitez pas que la transformation affecte la disposition, utilisez le <xref:System.Windows.FrameworkElement.LayoutTransform%2A> propriété de l’élément.  
  
 L’exemple suivant applique un <xref:System.Windows.Media.ScaleTransform> à la <xref:System.Windows.UIElement.RenderTransform%2A> propriété d’un bouton. Lorsque la souris se déplace sur le bouton, le <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> propriétés de la <xref:System.Windows.Media.ScaleTransform> sont définies sur `2`, ce qui entraîne le bouton plus grand. Lorsque la souris se déplace hors du bouton, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> et <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> sont définies sur `1`, ce qui entraîne le bouton pour revenir à sa taille d’origine.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[ButtonTransform#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [Vue d’ensemble des transformations](transforms-overview.md)
- [Rubriques de guide pratique](transformations-how-to-topics.md)
- [Vue d’ensemble des événements routés](../advanced/routed-events-overview.md)
