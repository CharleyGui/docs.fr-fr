---
title: 'Comment : traduire un élément'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: addff0e22fb3f27ea924887809c0635aeb3ad67d
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111970"
---
# <a name="how-to-translate-an-element"></a>Comment : traduire un élément
Cet exemple montre comment traduire (déplacer) <xref:System.Windows.Media.TranslateTransform>un élément en utilisant un .  
  
 La <xref:System.Windows.Media.TranslateTransform> classe est particulièrement utile pour déplacer des éléments à l’intérieur des panneaux qui ne prennent pas en charge le positionnement absolu. Par exemple, en <xref:System.Windows.Media.TranslateTransform> appliquant un élément à la <xref:System.Windows.UIElement.RenderTransform%2A> propriété <xref:System.Windows.Controls.StackPanel> d’un élément, vous pouvez déplacer un élément dans un ou <xref:System.Windows.Controls.DockPanel>.  
  
 Utilisez <xref:System.Windows.Media.TranslateTransform.X%2A> la propriété <xref:System.Windows.Media.TranslateTransform> de la pour spécifier la quantité, en pixels, pour déplacer l’élément le long de l’axe x. Utilisez <xref:System.Windows.Media.TranslateTransform.Y%2A> la propriété pour spécifier la quantité, en pixels, pour déplacer l’élément le long de l’axe y. Enfin, appliquez <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.UIElement.RenderTransform%2A> la propriété de l’élément.  
  
 L’exemple suivant <xref:System.Windows.Media.TranslateTransform> utilise un pour déplacer un élément de 50 pixels vers la droite et 50 pixels vers le bas.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 Pour l’échantillon complet, voir [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des transformations](transforms-overview.md)
