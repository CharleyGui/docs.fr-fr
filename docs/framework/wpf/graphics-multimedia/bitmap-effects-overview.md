---
title: Vue d'ensemble des effets bitmap
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 4a5e73f21d4ce4988f56c139d13038dca902b5b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186995"
---
# <a name="bitmap-effects-overview"></a>Vue d'ensemble des effets bitmap
Les effets Bitmap permettent aux concepteurs et aux développeurs d’appliquer des effets visuels au contenu rendu de la Windows Presentation Foundation (WPF). Par exemple, les effets de bitmap vous permettent d’appliquer facilement un <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> effet ou un effet de flou sur une image ou un bouton.  
  
> [!IMPORTANT]
> Dans le cadre .NET 4 <xref:System.Windows.Media.Effects.BitmapEffect> ou plus tard, la classe est obsolète. Si vous essayez <xref:System.Windows.Media.Effects.BitmapEffect> d’utiliser la classe, vous obtiendrez une exception obsolète. L’alternative non obsolète <xref:System.Windows.Media.Effects.BitmapEffect> à <xref:System.Windows.Media.Effects.Effect> la classe est la classe. Dans la plupart <xref:System.Windows.Media.Effects.Effect> des cas, la classe est beaucoup plus rapide.  

<a name="wpf_effects"></a>
## <a name="wpf-bitmap-effects"></a>Effets bitmap WPF  
 Les effets Bitmap (objet)<xref:System.Windows.Media.Effects.BitmapEffect> sont de simples opérations de traitement de pixels. Un effet bitmap <xref:System.Windows.Media.Imaging.BitmapSource> prend un comme <xref:System.Windows.Media.Imaging.BitmapSource> entrée et produit un nouveau après l’application de l’effet, comme un flou ou une ombre de chute. Chaque effet de bitmap expose les propriétés qui <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> <xref:System.Windows.Media.Effects.BlurBitmapEffect>peuvent contrôler les propriétés de filtrage, telles que de .  
  
 Comme un cas [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]particulier, en , les <xref:System.Windows.Media.Visual> effets peuvent être <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.TextBox>définis comme des propriétés sur des objets vivants, tels que a ou . Le traitement de pixels est appliqué et restitué au moment de l’exécution. Dans ce cas, au moment du <xref:System.Windows.Media.Visual> rendu, a <xref:System.Windows.Media.Imaging.BitmapSource> est automatiquement converti à <xref:System.Windows.Media.Effects.BitmapEffect>son équivalent et est alimenté comme entrée à la . La sortie remplace <xref:System.Windows.Media.Visual> le comportement de rendu par défaut de l’objet. C’est <xref:System.Windows.Media.Effects.BitmapEffect> pourquoi les objets forcent les visuels à rendre dans le logiciel seulement, c’est-à-dire aucune accélération matérielle sur les visuels lorsque les effets sont appliqués.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect>simule un objet qui apparaît hors de propos.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect>crée un halo de couleur autour du périmètre d’un objet.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>crée une ombre derrière un objet.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect>crée un biseau qui élève la surface d’une image selon une courbe spécifiée.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect>crée une cartographie <xref:System.Windows.Media.Visual> de bosse d’un pour donner l’impression de profondeur et de texture à partir d’une source de lumière artificielle.  
  
> [!NOTE]
> Les effets de bitmap WPF sont rendus en mode logiciel. Tout objet qui applique un effet est également rendu dans le logiciel. Les performances se dégradent le plus lors de l’utilisation des effets Bitmap sur les grands visuels ou de l’animation de propriétés d’un effet Bitmap. Cela ne signifie ne pas que ne vous ne devez pas utiliser les effets Bitmap de cette façon du tout, mais que vous devez les utiliser avec précaution et effectuer des tests approfondis pour vous assurer que vos utilisateurs obtiennent l’expérience que vous attendez.  
  
> [!NOTE]
> Les effets de bitmap WPF ne prennent pas en charge l’exécution partielle de la confiance. Une application doit avoir des autorisations de confiance totale pour utiliser des effets bitmap.  
  
<a name="applyeffects"></a>
## <a name="how-to-apply-an-effect"></a>Guide d’application d’un effet  
 <xref:System.Windows.Media.Effects.BitmapEffect>est une <xref:System.Windows.Media.Visual>propriété sur . Par conséquent, l’application d’effets <xref:System.Windows.Media.DrawingVisual>à <xref:System.Windows.UIElement>Visuals, tels que un <xref:System.Windows.Controls.Button>, , <xref:System.Windows.Controls.Image>, ou , est aussi facile que de définir une propriété. <xref:System.Windows.UIElement.BitmapEffect%2A>peut être réglé <xref:System.Windows.Media.Effects.BitmapEffect> sur un seul objet ou des <xref:System.Windows.Media.Effects.BitmapEffectGroup> effets multiples peuvent être enchaînés à l’aide de l’objet.  
  
 L’exemple suivant montre comment <xref:System.Windows.Media.Effects.BitmapEffect> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]appliquer un in .  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 L’exemple suivant montre comment <xref:System.Windows.Media.Effects.BitmapEffect> appliquer un code dans.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> Lorsqu’un <xref:System.Windows.Media.Effects.BitmapEffect> récipient de mise en <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Canvas>page est appliqué à un récipient de mise en page, tel que ou, l’effet est appliqué à l’arbre visuel de l’élément ou visuel, y compris tous ses éléments enfant.  
  
<a name="customeffects"></a>
## <a name="creating-custom-effects"></a>Création d'effets personnalisés  
 WPF fournit également des interfaces non gérées pour créer des effets personnalisés qui peuvent être utilisés dans les applications WPF gérées. Pour des documents de référence supplémentaires pour la création d’effets bitmap personnalisés, consultez la documentation [Effet bitmap WPF non managé](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Effet bitmap WPF non managé](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Vue d’ensemble de la création d’images](imaging-overview.md)
- [Sécurité](../security-wpf.md)
- [Vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md)
- [Graphisme 2D et acquisition d’images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
