---
title: 'Comment : créer du texte avec une ombre'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: c3e8135372ce4a092552c812cd971cb70bc49bf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186847"
---
# <a name="how-to-create-text-with-a-shadow"></a>Comment : créer du texte avec une ombre
Les exemples de cette section indiquent comment créer un effet d’ombre pour du texte affiché.  
  
## <a name="example"></a> Exemple  
 L’objet <xref:System.Windows.Media.Effects.DropShadowEffect> vous permet de créer une [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] variété d’effets d’ombre de chute pour les objets. L’exemple suivant présente un effet d’ombre portée appliqué au texte. Dans ce cas, l’ombre est une ombre légère, ce qui signifie que sa couleur devient floue.  
  
 ![Ombre de texte avec douceur &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg)
  
 Vous pouvez contrôler la largeur d’une ombre en définissant la <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> propriété. Une valeur `4.0` d’indique une largeur d’ombre de 4 pixels. Vous pouvez contrôler la douceur, ou le flou, <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> d’une ombre en modifiant la propriété. Une valeur `0.0` de n’indique aucun flou. L’exemple de code suivant montre comment créer une ombre légère.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> Ces effets d’ombre [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ne passent pas par le pipeline de rendu de texte. En conséquence, ClearType est désactivé lors de l’utilisation de ces effets.  
  
 L’exemple suivant présente un effet d’ombre portée marquée appliqué au texte. Dans ce cas, l’ombre n’est pas floue.  
  
 ![Ombre de texte avec douceur &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg)
  
 Vous pouvez créer une ombre <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> dure `0.0`en définissant la propriété à , ce qui indique qu’aucun flou n’est utilisé. Vous pouvez contrôler la direction de <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> l’ombre en modifiant la propriété. Définissez la valeur directionnelle de `0` cette `360`propriété dans une certaine mesure entre et . L’illustration suivante montre les <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> valeurs directionnelles du cadre de propriété.  
  
 ![Paramètre de degré DropShadow de l’ombre](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 L’exemple de code suivant montre comment créer une ombre marquée.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Utilisation d’un effet de flou  
 A <xref:System.Windows.Media.Effects.BlurBitmapEffect> peut être utilisé pour créer un effet d’ombre qui peut être placé derrière un objet de texte. Un effet bitmap flou appliqué au texte rend le texte flou uniformément dans toutes les directions.  
  
 L’exemple suivant présente un effet de flou appliqué au texte.  
  
 ![Ombre du texte utilisant BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 L’exemple de code suivant montre comment créer un effet de flou.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Utilisation d’une transformation de traduction  
 A <xref:System.Windows.Media.TranslateTransform> peut être utilisé pour créer un effet d’ombre qui peut être placé derrière un objet de texte.  
  
 L’exemple de <xref:System.Windows.Media.TranslateTransform> code suivant utilise un texte de compensation. Dans cet exemple, une copie légèrement décalée de texte en dessous du texte principal crée un effet d’ombre.  
  
 ![Ombre du texte utilisant TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)
  
 L’exemple de code suivant indique comment créer une transformation pour un effet d’ombre.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
