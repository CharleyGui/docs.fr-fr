---
title: Vue d'ensemble des effets bitmap
ms.date: 03/30/2017
helpviewer_keywords:
- bitmap effects [WPF]
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
ms.openlocfilehash: 4a5c304363efe7d0e9bd9e14ff916f8d852ab3a8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636014"
---
# <a name="bitmap-effects-overview"></a>Vue d'ensemble des effets bitmap
Les effets bitmap permettent aux concepteurs et aux développeurs d’appliquer des effets visuels au contenu Windows Presentation Foundation (WPF) rendu. Par exemple, les effets bitmap vous permettent d’appliquer facilement un effet de <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> ou un effet de flou à une image ou un bouton.  
  
> [!IMPORTANT]
> Dans le .NET Framework 4 ou version ultérieure, la classe <xref:System.Windows.Media.Effects.BitmapEffect> est obsolète. Si vous essayez d’utiliser la classe <xref:System.Windows.Media.Effects.BitmapEffect>, vous obtiendrez une exception obsolète. L’alternative non obsolète à la classe <xref:System.Windows.Media.Effects.BitmapEffect> est la classe <xref:System.Windows.Media.Effects.Effect>. Dans la plupart des cas, la classe <xref:System.Windows.Media.Effects.Effect> est beaucoup plus rapide.  

<a name="wpf_effects"></a>   
## <a name="wpf-bitmap-effects"></a>Effets bitmap WPF  
 Les effets bitmap (objet<xref:System.Windows.Media.Effects.BitmapEffect>) sont des opérations de traitement de pixels simples. Un effet bitmap prend une <xref:System.Windows.Media.Imaging.BitmapSource> comme entrée et produit une nouvelle <xref:System.Windows.Media.Imaging.BitmapSource> après avoir appliqué l’effet, tel qu’un flou ou une ombre portée. Chaque effet bitmap expose des propriétés qui peuvent contrôler les propriétés de filtrage, telles que <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> de <xref:System.Windows.Media.Effects.BlurBitmapEffect>.  
  
 En guise de cas particulier, dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les effets peuvent être définis en tant que propriétés sur des objets de <xref:System.Windows.Media.Visual> en direct, tels qu’un <xref:System.Windows.Controls.Button> ou <xref:System.Windows.Controls.TextBox>. Le traitement de pixels est appliqué et restitué au moment de l’exécution. Dans ce cas, au moment du rendu, un <xref:System.Windows.Media.Visual> est automatiquement converti en son équivalent <xref:System.Windows.Media.Imaging.BitmapSource> et est chargé comme entrée pour le <xref:System.Windows.Media.Effects.BitmapEffect>. La sortie remplace le comportement de rendu par défaut de l’objet <xref:System.Windows.Media.Visual>. C’est la raison pour laquelle <xref:System.Windows.Media.Effects.BitmapEffect> objets forcent le rendu des éléments visuels dans les logiciels uniquement, c’est-à-dire aucune accélération matérielle sur les visuels lorsque des effets sont appliqués.  
  
- <xref:System.Windows.Media.Effects.BlurBitmapEffect> simule un objet qui semble prêt à l’emploi.  
  
- <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> crée un halo de couleur autour du périmètre d’un objet.  
  
- <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> crée une ombre derrière un objet.  
  
- <xref:System.Windows.Media.Effects.BevelBitmapEffect> crée un biseau qui lève la surface d’une image en fonction d’une courbe spécifiée.  
  
- <xref:System.Windows.Media.Effects.EmbossBitmapEffect> crée un placage de relief d’une <xref:System.Windows.Media.Visual> pour fournir l’impression de profondeur et de texture à partir d’une source de lumière artificielle.  
  
> [!NOTE]
> Les effets bitmap WPF sont rendus en mode logiciel. Tout objet qui applique un effet est également rendu dans le logiciel. Les performances se dégradent le plus lors de l’utilisation des effets Bitmap sur les grands visuels ou de l’animation de propriétés d’un effet Bitmap. Cela ne signifie ne pas que ne vous ne devez pas utiliser les effets Bitmap de cette façon du tout, mais que vous devez les utiliser avec précaution et effectuer des tests approfondis pour vous assurer que vos utilisateurs obtiennent l’expérience que vous attendez.  
  
> [!NOTE]
> Les effets bitmap WPF ne prennent pas en charge l’exécution de la confiance partielle. Une application doit avoir des autorisations de confiance totale pour utiliser des effets bitmap.  
  
<a name="applyeffects"></a>   
## <a name="how-to-apply-an-effect"></a>Guide d’application d’un effet  
 <xref:System.Windows.Media.Effects.BitmapEffect> est une propriété sur <xref:System.Windows.Media.Visual>. Par conséquent, l’application d’effets aux éléments visuels, tels qu’un <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>ou <xref:System.Windows.UIElement>, est aussi simple que la définition d’une propriété. <xref:System.Windows.UIElement.BitmapEffect%2A> peut être défini sur un seul objet <xref:System.Windows.Media.Effects.BitmapEffect> ou plusieurs effets peuvent être chaînés à l’aide de l’objet <xref:System.Windows.Media.Effects.BitmapEffectGroup>.  
  
 L’exemple suivant montre comment appliquer une <xref:System.Windows.Media.Effects.BitmapEffect> dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xaml[EffectsGallery_snip#BlurSimpleExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 L’exemple suivant montre comment appliquer une <xref:System.Windows.Media.Effects.BitmapEffect> dans le code.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
> Lorsqu’un <xref:System.Windows.Media.Effects.BitmapEffect> est appliqué à un conteneur de disposition, tel que <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.Canvas>, l’effet est appliqué à l’arborescence d’éléments visuels de l’élément ou de l’élément visuel, y compris tous ses éléments enfants.  
  
<a name="customeffects"></a>   
## <a name="creating-custom-effects"></a>Création d'effets personnalisés  
 WPF fournit également des interfaces non managées pour créer des effets personnalisés qui peuvent être utilisés dans les applications WPF managées. Pour des documents de référence supplémentaires pour la création d’effets bitmap personnalisés, consultez la documentation [Effet bitmap WPF non managé](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Effects.BitmapEffectGroup>
- <xref:System.Windows.Media.Effects.BitmapEffectInput>
- <xref:System.Windows.Media.Effects.BitmapEffectCollection>
- [Effet bitmap WPF non managé](https://docs.microsoft.com/previous-versions/windows/desktop/wibe/-wibe-lh)
- [Vue d’ensemble de la création d’images](imaging-overview.md)
- [Security](../security-wpf.md)
- [Vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md)
- [Graphiques 2D et acquisition d'images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
