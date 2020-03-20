---
title: 'Comment : appliquer des transformations à du texte'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: 867f39e3df8493014d8601530e91310c3bbbeeb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141612"
---
# <a name="how-to-apply-transforms-to-text"></a>Comment : appliquer des transformations à du texte
Les transformations peuvent modifier l’affichage de texte dans votre application. Les exemples suivants utilisent différents types de transformations de <xref:System.Windows.Controls.TextBlock> rendu pour affecter l’affichage du texte dans un contrôle.  
  
## <a name="example"></a> Exemple  
 L’exemple suivant présente un texte pivoté par rapport à un point spécifié dans le plan x-y à deux dimensions.  
  
 ![Texte pivoté à l'aide de RotateTransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 L’exemple de <xref:System.Windows.Media.RotateTransform> code suivant utilise un texte de rotation. Une <xref:System.Windows.Media.RotateTransform.Angle%2A> valeur de 90 tourne l’élément 90 degrés dans le sens des aiguilles d’une montre.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Dans l’exemple suivant, la deuxième ligne du texte est mise à l’échelle par 150 % le long de l’axe x et la troisième ligne du texte est mise à l’échelle par 150 % le long de l’axe y.  
  
 ![Texte mis à l'échelle à l'aide de ScaleTransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg)
  
 L’exemple de <xref:System.Windows.Media.ScaleTransform> code suivant utilise un texte à l’échelle de sa taille d’origine.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> La mise à l’échelle du texte est différente de l’augmentation de la taille de police du texte. Les tailles de police sont calculées indépendamment les unes des autres pour fournir la meilleure résolution à des tailles différentes. Le texte mis à l’échelle, en revanche, conserve les proportions du texte à la taille d’origine.  
  
 L’exemple suivant présente le texte incliné le long de l’axe x.  
  
 ![Texte incliné à l'aide de SkewTransform](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)

 L’exemple de <xref:System.Windows.Media.SkewTransform> code suivant utilise un texte biaisé. Une inclinaison est une transformation qui étire l’espace de coordonnées de façon non uniforme. Dans cet exemple, les deux chaînes de texte sont inclinées de -30° et 30° le long de la coordonnée x.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 L’exemple suivant présente le texte traduit ou déplacé, le long des axes x et y.  
  
 ![Décalage de texte utilisant TranslateTransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 L’exemple de <xref:System.Windows.Media.TranslateTransform> code suivant utilise un texte de compensation. Dans cet exemple, une copie légèrement décalée de texte en dessous du texte principal crée un effet d’ombre.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> Le <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> fournit un riche ensemble de fonctionnalités pour fournir des effets d’ombre. Pour plus d’informations, voir [Créer du texte avec une ombre](how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Voir aussi

- [Appliquer des animations à du texte](how-to-apply-animations-to-text.md)
