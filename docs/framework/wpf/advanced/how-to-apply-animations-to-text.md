---
title: 'Comment : appliquer des animations à du texte'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: ed2f3beb904f724ac93e2c4033aa6b2eb3fa1290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174626"
---
# <a name="how-to-apply-animations-to-text"></a>Comment : appliquer des animations à du texte
Les animations peuvent modifier l’affichage et l’apparence du texte dans votre application. Les exemples suivants utilisent différents types d’animations <xref:System.Windows.Controls.TextBlock> pour affecter l’affichage du texte dans un contrôle.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation> utilise un pour animer la largeur du bloc de texte. La valeur de largeur change pour passer de la largeur du bloc de texte à 0 sur une durée de 10 secondes, puis les valeurs de largeur sont inversées et la procédure continue. Ce type d’animation crée un effet de balayage.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation> utilise un pour animer l’opacité du bloc de texte. La valeur d’opacité passe de 1.0 à 0 sur une durée de 5 secondes, puis les valeurs d’opacité sont inversées et la procédure continue.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 Le diagramme suivant montre <xref:System.Windows.Controls.TextBlock> l’effet du contrôle `1.00` `0.00` changeant son opacité de <xref:System.Windows.Media.Animation.Timeline.Duration%2A>à l’intervalle de 5 secondes défini par le .  
  
 ![Opacité changeant de texte de 1.00 à 0.00.](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  

 L’exemple suivant <xref:System.Windows.Media.Animation.ColorAnimation> utilise un pour animer la couleur de premier plan du bloc de texte. La valeur de la couleur de premier plan passe d’une couleur à une autre sur une durée de 5 secondes, puis les valeurs de couleur sont inversées et la procédure continue.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation> utilise un pour faire pivoter le bloc de texte. Le bloc de texte effectue une rotation complète sur une durée de 20 secondes, puis la procédure de rotation se répète.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](../graphics-multimedia/animation-overview.md)
