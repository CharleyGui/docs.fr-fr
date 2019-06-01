---
title: Vue d'ensemble des effets bitmap
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: ccf837bd9f0e0bb40cfb07d5eeaa1f0f80a86ca9
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456686"
---
# <a name="bitmap-effects-overview"></a>Vue d'ensemble des effets bitmap
Effets bitmap permettent aux concepteurs et aux développeurs d’appliquer des effets visuels pour Windows Presentation Foundation (WPF) contenu rendu. Par exemple, effets bitmap vous permettent d’appliquer facilement un <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> effet ou un effet de flou à une image ou un bouton.  
  
> [!IMPORTANT]
>  Dans le .NET Framework 4 ou version ultérieure, la <xref:System.Windows.Media.Effects.BitmapEffect> classe est obsolète. Si vous essayez d’utiliser le <xref:System.Windows.Media.Effects.BitmapEffect> (classe), vous obtiendrez une exception obsolète. L’alternative non obsolète à la <xref:System.Windows.Media.Effects.BitmapEffect> classe est la <xref:System.Windows.Media.Effects.Effect> classe. Dans la plupart des cas, la <xref:System.Windows.Media.Effects.Effect> classe est beaucoup plus rapide.  

<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>Effets bitmap WPF  
 Effets bitmap (<xref:System.Windows.Media.Effects.BitmapEffect> objet) sont des opérations de traitement de pixels simples. Un effet bitmap prend un <xref:System.Windows.Media.Imaging.BitmapSource> comme entrée et produit un nouveau <xref:System.Windows.Media.Imaging.BitmapSource> après avoir appliqué l’effet, par exemple un flou ou une ombre portée. Chaque effet bitmap expose des propriétés qui peuvent contrôler les propriétés de filtrage, telles que <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> de <xref:System.Windows.Media.Effects.BlurBitmapEffect>.  
  
 Comme un cas particulier, dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], effets peuvent être définis en tant que propriétés sur live <xref:System.Windows.Media.Visual> objets, tels qu’un <xref:System.Windows.Controls.Button> ou <xref:System.Windows.Controls.TextBox>. Le traitement de pixels est appliqué et restitué au moment de l’exécution. Dans ce cas, au moment du rendu, un <xref:System.Windows.Media.Visual> est automatiquement convertie en son <xref:System.Windows.Media.Imaging.BitmapSource> équivalent et acheminé comme entrée pour le <xref:System.Windows.Media.Effects.BitmapEffect>. La sortie remplace le <xref:System.Windows.Media.Visual> comportement de rendu par défaut de l’objet. C’est pourquoi <xref:System.Windows.Media.Effects.BitmapEffect> objets forcent le rendu logiciel seulement, c'est-à-dire sans accélération matérielle sur les visuels lorsque des effets sont appliqués.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect> simule un objet qui s’affiche hors du focus.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> Crée un halo de couleur autour du périmètre d’un objet.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Crée une ombre derrière un objet.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect> Crée un biseau qui élève la surface d’une image selon une courbe spécifiée.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect> Crée un placage de relief un <xref:System.Windows.Media.Visual> pour donner une impression de profondeur et de texture à partir d’une source de lumière artificielle.  
  
> [!NOTE]
>  Les effets bitmap [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sont restitués en mode logiciel. Tout objet qui applique un effet est également rendu dans le logiciel. Les performances se dégradent le plus lors de l’utilisation des effets Bitmap sur les grands visuels ou de l’animation de propriétés d’un effet Bitmap. Cela ne signifie ne pas que ne vous ne devez pas utiliser les effets Bitmap de cette façon du tout, mais que vous devez les utiliser avec précaution et effectuer des tests approfondis pour vous assurer que vos utilisateurs obtiennent l’expérience que vous attendez.  
  
> [!NOTE]
>  Les effets bitmap [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ne gèrent pas l’exécution en mode confiance partielle. Une application doit avoir des autorisations de confiance totale pour utiliser des effets bitmap.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Guide d’application d’un effet  
 <xref:System.Windows.Media.Effects.BitmapEffect> est une propriété de <xref:System.Windows.Media.Visual>. Par conséquent, application d’effets aux visuels, comme un <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>, ou <xref:System.Windows.UIElement>, est aussi simple que la définition d’une propriété. <xref:System.Windows.UIElement.BitmapEffect%2A> peut être définie sur un seul <xref:System.Windows.Media.Effects.BitmapEffect> objet ou plusieurs effets peuvent être chaînés à l’aide de la <xref:System.Windows.Media.Effects.BitmapEffectGroup> objet.  
  
 L’exemple suivant montre comment appliquer un <xref:System.Windows.Media.Effects.BitmapEffect> dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 L’exemple suivant montre comment appliquer un <xref:System.Windows.Media.Effects.BitmapEffect> dans le code.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  Quand un <xref:System.Windows.Media.Effects.BitmapEffect> est appliquée à un conteneur de disposition, telle que <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.Canvas>, l’effet est appliqué à l’arborescence visuelle de l’élément ou d’un visuel, y compris tous ses éléments enfants.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Création d'effets personnalisés  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit également des interfaces non managées pour créer des effets personnalisés qui peuvent être utilisés dans les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] managées. Pour des documents de référence supplémentaires pour la création d’effets bitmap personnalisés, consultez la documentation [Effet bitmap WPF non managé](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Effet Bitmap WPF non managé](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Vue d’ensemble de la création d’images](imaging-overview.md)
- [Sécurité](../security-wpf.md)
- [Vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md)
- [Graphiques 2D et acquisition d'images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
