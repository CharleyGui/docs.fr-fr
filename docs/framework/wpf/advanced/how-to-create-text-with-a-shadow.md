---
title: 'Procédure : Créer du texte avec une ombre'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 0fe64e4e9e7aadbd30a38743647251f9fa49ba95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960438"
---
# <a name="how-to-create-text-with-a-shadow"></a>Procédure : Créer du texte avec une ombre
Les exemples de cette section indiquent comment créer un effet d’ombre pour du texte affiché.  
  
## <a name="example"></a>Exemples  
 L' <xref:System.Windows.Media.Effects.DropShadowEffect> objet vous permet de créer divers effets d’ombre portée pour les [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objets. L’exemple suivant présente un effet d’ombre portée appliqué au texte. Dans ce cas, l’ombre est une ombre légère, ce qui signifie que sa couleur devient floue.  
  
 ![Ombre du texte avec adoucissement &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 Vous pouvez contrôler la largeur d’une ombre en définissant <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> la propriété. La valeur `4.0` indique une largeur de l’ombre de 4 pixels. Vous pouvez contrôler l’adoucissement ou le flou d’une ombre en modifiant la <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriété. La valeur indique `0.0` l’absence de flou. L’exemple de code suivant montre comment créer une ombre légère.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> Ces effets d’ombre ne passent pas par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] le pipeline de rendu de texte. En conséquence, ClearType est désactivé lors de l’utilisation de ces effets.  
  
 L’exemple suivant présente un effet d’ombre portée marquée appliqué au texte. Dans ce cas, l’ombre n’est pas floue.  
  
 ![Ombre du texte avec adoucissement &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 Vous pouvez créer une ombre dure en affectant <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> à `0.0`la propriété la valeur, ce qui indique qu’aucun flou n’est utilisé. Vous pouvez contrôler la direction de l’ombre en modifiant la <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> propriété. Définissez la valeur directionnelle de cette propriété sur un degré entre `0` et `360`. L’illustration suivante montre les valeurs directionnelles du <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> paramètre de propriété.  
  
 ![Paramètre de degré DropShadow de l’ombre](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 L’exemple de code suivant montre comment créer une ombre marquée.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a>Utilisation d’un effet de flou  
 Un <xref:System.Windows.Media.Effects.BlurBitmapEffect> peut être utilisé pour créer un effet similaire à une ombre pouvant être placé derrière un objet de texte. Un effet bitmap flou appliqué au texte rend le texte flou uniformément dans toutes les directions.  
  
 L’exemple suivant présente un effet de flou appliqué au texte.  
  
 ![Ombre du texte utilisant BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 L’exemple de code suivant montre comment créer un effet de flou.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a>Utilisation d’une transformation de traduction  
 Un <xref:System.Windows.Media.TranslateTransform> peut être utilisé pour créer un effet similaire à une ombre pouvant être placé derrière un objet de texte.  
  
 L’exemple de code suivant utilise <xref:System.Windows.Media.TranslateTransform> un pour décaler le texte. Dans cet exemple, une copie légèrement décalée de texte en dessous du texte principal crée un effet d’ombre.  
  
 ![Ombre du texte utilisant TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 L’exemple de code suivant indique comment créer une transformation pour un effet d’ombre.  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
