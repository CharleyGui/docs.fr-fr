---
title: 'Comment : appliquer plusieurs transformations à un objet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
ms.openlocfilehash: 3ef11104b2a4fc775d29d2a388c9a70a69a3f10f
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112113"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a>Comment : appliquer plusieurs transformations à un objet
Cet exemple montre comment <xref:System.Windows.Media.TransformGroup> utiliser un <xref:System.Windows.Media.Transform> groupe de deux <xref:System.Windows.Media.Transform>objets ou plus dans un seul composite .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant <xref:System.Windows.Media.TransformGroup> utilise <xref:System.Windows.Media.ScaleTransform> un <xref:System.Windows.Media.RotateTransform> pour <xref:System.Windows.Controls.Button>appliquer a et a à un .  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [Vue d'ensemble des transformations](transforms-overview.md)
- [2D transforme l’échantillon](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
