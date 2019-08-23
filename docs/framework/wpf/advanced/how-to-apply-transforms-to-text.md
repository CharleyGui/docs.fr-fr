---
title: 'Procédure : Appliquer des transformations à du texte'
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
ms.openlocfilehash: b749d21c1b5940d216e244393eeb3c133dc153b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956482"
---
# <a name="how-to-apply-transforms-to-text"></a>Procédure : Appliquer des transformations à du texte
Les transformations peuvent modifier l’affichage de texte dans votre application. Les exemples suivants utilisent différents types de transformations de rendu pour affecter l’affichage du texte dans <xref:System.Windows.Controls.TextBlock> un contrôle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant présente un texte pivoté par rapport à un point spécifié dans le plan x-y à deux dimensions.  
  
 ![Texte pivoté à l'aide de RotateTransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 L’exemple de code suivant utilise <xref:System.Windows.Media.RotateTransform> un pour faire pivoter du texte. Une <xref:System.Windows.Media.RotateTransform.Angle%2A> valeur de 90 fait pivoter l’élément de 90 degrés dans le sens des aiguilles d’une montre.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Dans l’exemple suivant, la deuxième ligne du texte est mise à l’échelle par 150 % le long de l’axe x et la troisième ligne du texte est mise à l’échelle par 150 % le long de l’axe y.  
  
 ![Texte mis à l'échelle à l'aide de ScaleTransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg) 
  
 L’exemple de code suivant utilise <xref:System.Windows.Media.ScaleTransform> un pour mettre à l’échelle du texte à partir de sa taille d’origine.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> La mise à l’échelle du texte est différente de l’augmentation de la taille de police du texte. Les tailles de police sont calculées indépendamment les unes des autres pour fournir la meilleure résolution à des tailles différentes. Le texte mis à l’échelle, en revanche, conserve les proportions du texte à la taille d’origine.  
  
 L’exemple suivant présente le texte incliné le long de l’axe x.  
  
 ![Texte incliné à l'aide de SkewTransform](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)
   
 L’exemple de code suivant utilise <xref:System.Windows.Media.SkewTransform> un pour incliner le texte. Une inclinaison est une transformation qui étire l’espace de coordonnées de façon non uniforme. Dans cet exemple, les deux chaînes de texte sont inclinées de -30° et 30° le long de la coordonnée x.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 L’exemple suivant présente le texte traduit ou déplacé, le long des axes x et y.  
  
 ![Décalage de texte utilisant TranslateTransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 L’exemple de code suivant utilise <xref:System.Windows.Media.TranslateTransform> un pour décaler le texte. Dans cet exemple, une copie légèrement décalée de texte en dessous du texte principal crée un effet d’ombre.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Fournit un ensemble complet de fonctionnalités pour fournir des effets d’ombre. Pour plus d’informations, consultez [créer du texte avec une ombre](how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour appliquer des animations à du texte](how-to-apply-animations-to-text.md)
