---
title: Vue d’ensemble des animations from-to-by
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 661c035f55ba1fb550726d75921cd01a72b2eecc
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448998"
---
# <a name="fromtoby-animations-overview"></a>Vue d'ensemble des animations From/To/By
Cette rubrique explique comment utiliser des animations From/To/By pour animer des propriétés de dépendance. Une animation From/To/By crée une transition entre deux valeurs.  
  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour comprendre cette rubrique, vous devez être familiarisé avec les fonctionnalités d’animation de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pour une présentation des fonctionnalités d’animation, consultez [vue d’ensemble](animation-overview.md)de l’animation.  
  
<a name="whatisanimation"></a>   
## <a name="what-is-a-fromtoby-animation"></a>Qu’est-ce qu’une animation From/To/By ?  
 Une animation from/to/by est un type de <xref:System.Windows.Media.Animation.AnimationTimeline> qui crée une transition entre une valeur de début et une valeur de fin. La durée d’exécution de la transition est déterminée par le <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cette animation.  
  
 Vous pouvez appliquer une animation from/to/by à une propriété à l’aide d’une <xref:System.Windows.Media.Animation.Storyboard> dans le balisage et le code, ou à l’aide de la méthode <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> dans le code. Vous pouvez également utiliser une animation from/to/by pour créer un <xref:System.Windows.Media.Animation.AnimationClock> et l’appliquer à une ou plusieurs propriétés. Pour plus d’informations sur les différentes façons d’appliquer des animations, consultez la [Vue d’ensemble des techniques d’animation de propriétés](property-animation-techniques-overview.md).  
  
 Les animations From/To/By ne peuvent pas avoir plus de deux valeurs cibles. Si vous avez besoin d’une animation comportant plus de deux valeurs cibles, utilisez une animation d’image clé. Les animations d’image clé sont décrites dans [vue d’ensemble des animations d’image clé](key-frame-animations-overview.md).  
  
<a name="animation_types"></a>   
## <a name="fromtoby-animation-types"></a>Types d’animation From/To/By  
 Étant donné que les animations génèrent des valeurs de propriété, il existe différents types d’animation pour différents types de propriété. Pour animer une propriété qui prend une <xref:System.Double>, telle que la propriété <xref:System.Windows.FrameworkElement.Width%2A> d’un élément, utilisez une animation qui produit des valeurs de <xref:System.Double>. Pour animer une propriété qui prend un <xref:System.Windows.Point>, utilisez une animation qui produit des valeurs de <xref:System.Windows.Point>, et ainsi de suite.  
  
 Les classes d’animation from/to/by appartiennent à l’espace de noms <xref:System.Windows.Media.Animation> et utilisent la Convention d’affectation de noms suivante :  
  
 *type de\<>* `Animation`  
  
 Où *\<Type >* est le type de valeur que la classe anime.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit les classes d’animation From/To/By suivantes.  
  
|Type de propriété|Classe d’animations From/To/By correspondante|  
|-------------------|------------------------------------------------|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimation>|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimation>|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16Animation>|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32Animation>|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64Animation>|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimation>|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimation>|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimation>|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimation>|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimation>|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimation>|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimation>|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimation>|  
  
<a name="anim_values"></a>   
## <a name="target-values"></a>Valeurs cibles  
 Une animation From/To/By crée une transition entre deux valeurs cibles. Il est courant de spécifier une valeur de départ (définissez-la à l’aide de la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>) et une valeur de fin (définissez-la à l’aide de la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>). Toutefois, vous pouvez également spécifier uniquement une valeur de début, une valeur de destination ou une valeur de décalage. Dans ces cas, l’animation obtient la valeur cible manquante de la propriété qui est animée. La liste suivante décrit les différentes manières de spécifier les valeurs cibles d’une animation.  
  
- **Valeur de départ**  
  
     Utilisez la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> lorsque vous souhaitez spécifier explicitement la valeur de départ d’une animation. Vous pouvez utiliser la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> seule ou avec la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> ou <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>. Si vous spécifiez uniquement la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, l’animation passe de cette valeur à la valeur de base de la propriété animée.  
  
- **Valeur de fin**  
  
     Pour spécifier la valeur de fin d’une animation, utilisez sa propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>. Si vous utilisez la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> par elle-même, l’animation obtient sa valeur de départ à partir de la propriété animée ou de la sortie d’une autre animation appliquée à la même propriété. Vous pouvez utiliser la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> avec la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> pour spécifier explicitement les valeurs de début et de fin de l’animation.  
  
- **Valeur de décalage**  
  
     La propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> vous permet de spécifier un décalage à la place d’une valeur de début ou de fin explicite pour l’animation. La propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> d’une animation spécifie le degré de modification d’une valeur par l’animation sur sa durée. Vous pouvez utiliser la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> seule ou avec la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>. Si vous spécifiez uniquement la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>, l’animation ajoute la valeur de décalage à la valeur de base de la propriété ou à la sortie d’une autre animation.  
  
<a name="examples"></a>   
## <a name="using-fromtoby-values"></a>Utilisation des valeurs From/To/By  
 Les sections suivantes décrivent comment utiliser les propriétés <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> ensemble ou séparément.  
  
 Les exemples de cette section utilisent chacun un <xref:System.Windows.Media.Animation.DoubleAnimation>, qui est un type d’animation from/to/by, pour animer la propriété <xref:System.Windows.FrameworkElement.Width%2A> d’un <xref:System.Windows.Shapes.Rectangle> qui est 10 pixels indépendants du périphérique et 100 pixels indépendants du périphérique en largeur.  
  
 Bien que chaque exemple utilise un <xref:System.Windows.Media.Animation.DoubleAnimation>, les propriétés from, to et by de toutes les animations from/to/by se comportent de la même façon. Bien que chacun de ces exemples utilise une <xref:System.Windows.Media.Animation.Storyboard>, vous pouvez utiliser les animations from/to/by d’une autre manière. Pour plus d’informations, consultez [vue d’ensemble des techniques d’animation de propriétés](property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>De/À  
 Lorsque vous définissez les valeurs <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> ensemble, l’animation passe de la valeur spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, à la valeur spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.  
  
 L’exemple suivant affecte à la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> de la <xref:System.Windows.Media.Animation.DoubleAnimation> la valeur 50 et à sa propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> la valeur 300. Par conséquent, la <xref:System.Windows.FrameworkElement.Width%2A> du <xref:System.Windows.Shapes.Rectangle> est animée de 50 à 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>À  
 Lorsque vous définissez uniquement la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, l’animation passe de la valeur de base de la propriété animée ou de la sortie d’une animation de composition qui a été précédemment appliquée à la même propriété, à la valeur spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.  
  
 (« Composition d’animation » fait référence à une animation <xref:System.Windows.Media.Animation.ClockState.Active> ou <xref:System.Windows.Media.Animation.ClockState.Filling> précédemment appliquée à la même propriété qui est toujours en vigueur lorsque l’animation actuelle a été appliquée à l’aide du comportement de transfert <xref:System.Windows.Media.Animation.HandoffBehavior.Compose>.)  
  
 L’exemple suivant définit uniquement la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> du <xref:System.Windows.Media.Animation.DoubleAnimation> sur 300. Comme aucune valeur de départ n’a été spécifiée, le <xref:System.Windows.Media.Animation.DoubleAnimation> utilise la valeur de base (100) de la propriété <xref:System.Windows.FrameworkElement.Width%2A> comme valeur de départ. La <xref:System.Windows.FrameworkElement.Width%2A> du <xref:System.Windows.Shapes.Rectangle> est animée de 100 à la valeur cible de l’animation 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>par  
 Lorsque vous définissez uniquement la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> d’une animation, l’animation passe de la valeur de base de la propriété qui est animée, ou de la sortie d’une animation de composition à la somme de cette valeur et de la valeur spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  
  
 L’exemple suivant définit uniquement la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> du <xref:System.Windows.Media.Animation.DoubleAnimation> sur 300. Étant donné que l’exemple ne spécifie pas de valeur de départ, le <xref:System.Windows.Media.Animation.DoubleAnimation> utilise la valeur de base de la propriété <xref:System.Windows.FrameworkElement.Width%2A>, 100, comme valeur de départ. La valeur de fin est déterminée en ajoutant la valeur <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> de l’animation, 300, à sa valeur de départ, 100:400. Par conséquent, la <xref:System.Windows.FrameworkElement.Width%2A> du <xref:System.Windows.Shapes.Rectangle> est animée de 100 à 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>From/By  
 Lorsque vous définissez les propriétés <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> d’une animation, l’animation passe de la valeur spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, à la valeur spécifiée par la somme des propriétés <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  
  
 L’exemple suivant affecte à la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> de la <xref:System.Windows.Media.Animation.DoubleAnimation> la valeur 50 et à sa propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> la valeur 300. La valeur de fin est déterminée en ajoutant la valeur <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> de l’animation, 300, à sa valeur de départ, 50:350. Par conséquent, la <xref:System.Windows.FrameworkElement.Width%2A> du <xref:System.Windows.Shapes.Rectangle> est animée de 50 à 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>À partir  
 Lorsque vous spécifiez uniquement la valeur <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> d’une animation, l’animation passe de la valeur spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, à la valeur de base de la propriété animée ou à la sortie d’une animation de composition.  
  
 L’exemple suivant définit uniquement la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> du <xref:System.Windows.Media.Animation.DoubleAnimation> sur 50. Comme aucune valeur finale n’a été spécifiée, le <xref:System.Windows.Media.Animation.DoubleAnimation> utilise la valeur de base de la propriété <xref:System.Windows.FrameworkElement.Width%2A>, 100, comme valeur de fin. La <xref:System.Windows.FrameworkElement.Width%2A> du <xref:System.Windows.Shapes.Rectangle> est animée de 50 à la valeur de base de la propriété <xref:System.Windows.FrameworkElement.Width%2A>, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>To/By  
 Si vous définissez à la fois les propriétés <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> d’une animation, la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> est ignorée.  
  
<a name="otheranimationtypes"></a>   
## <a name="other-animation-types"></a>Autres types d’animations  
 Les animations from/to/by ne sont pas le seul type d’animation fourni par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] : elles fournissent également des animations d’image clé et des animations de tracés.  
  
- Une animation d’image clé est animée avec n’importe quel nombre de valeurs de destination et décrite à l’aide d’images clés. Pour plus d’informations, consultez [vue d’ensemble des animations d’image clé](key-frame-animations-overview.md).  
  
- Une animation de tracés génère des valeurs de sortie à partir d’un <xref:System.Windows.Media.PathGeometry>. Pour plus d’informations, consultez [vue d’ensemble des animations de tracés](path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet également de créer vos propres types d’animations personnalisées. Pour plus d’informations, consultez [vue d’ensemble des animations personnalisées](custom-animations-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des storyboards](storyboards-overview.md)
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Vue d'ensemble des animations de tracés](path-animations-overview.md)
- [Vue d'ensemble des animations personnalisées](custom-animations-overview.md)
- [Exemple de valeurs cibles d’animation From, To, and By Animation Target Values Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
