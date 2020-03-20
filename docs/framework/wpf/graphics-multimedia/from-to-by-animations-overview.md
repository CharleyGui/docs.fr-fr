---
title: Aperçu des animations de de -à-par
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], From/to/by
- From/to/by animation
ms.assetid: 516fce0a-e7f8-49b8-b018-53b3d409a8a3
ms.openlocfilehash: 135f01823d374b30f8d4d41762d2267a254f98c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186462"
---
# <a name="fromtoby-animations-overview"></a>Vue d'ensemble des animations From/To/By
Cette rubrique explique comment utiliser des animations From/To/By pour animer des propriétés de dépendance. Une animation From/To/By crée une transition entre deux valeurs.  
  
<a name="prereq"></a>
## <a name="prerequisites"></a>Conditions préalables requises  
 Pour comprendre ce sujet, vous [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] devez être familier avec les fonctionnalités d’animations. Pour une introduction aux fonctionnalités d’animation, voir [l’Aperçu de l’animation](animation-overview.md).  
  
<a name="whatisanimation"></a>
## <a name="what-is-a-fromtoby-animation"></a>Qu’est-ce qu’une animation From/To/By ?  
 Une animation De/To/By est <xref:System.Windows.Media.Animation.AnimationTimeline> un type qui crée une transition entre une valeur de départ et une valeur de fin. Le temps que la transition prend pour <xref:System.Windows.Media.Animation.Timeline.Duration%2A> terminer est déterminé par la de cette animation.  
  
 Vous pouvez appliquer une animation From/To/By <xref:System.Windows.Media.Animation.Storyboard> à une propriété en utilisant <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> un balisage et un code, ou en utilisant la méthode dans le code. Vous pouvez également utiliser un From/To/By Animation pour créer un <xref:System.Windows.Media.Animation.AnimationClock> et l’appliquer à une ou plusieurs propriétés. Pour plus d’informations sur les différentes méthodes d’application des animations, voir le [Aperçu des techniques d’animation de](property-animation-techniques-overview.md)propriété .  
  
 Les animations From/To/By ne peuvent pas avoir plus de deux valeurs cibles. Si vous avez besoin d’une animation comportant plus de deux valeurs cibles, utilisez une animation d’image clé. Les animations à cadre clé sont décrites dans le [Aperçu des animations Key-Frame](key-frame-animations-overview.md).  
  
<a name="animation_types"></a>
## <a name="fromtoby-animation-types"></a>Types d’animation From/To/By  
 Étant donné que les animations génèrent des valeurs de propriété, il existe différents types d’animation pour différents types de propriété. Pour animer une propriété <xref:System.Double>qui prend <xref:System.Windows.FrameworkElement.Width%2A> un , comme la propriété <xref:System.Double> d’un élément, utiliser une animation qui produit des valeurs. Pour animer une propriété <xref:System.Windows.Point>qui prend un <xref:System.Windows.Point> , utilisez une animation qui produit des valeurs, et ainsi de suite.  
  
 De/To/By cours d’animation appartiennent à l’espace <xref:System.Windows.Media.Animation> de nom et utilisent la convention de nommage suivante:  
  
 * \<Type>*`Animation`  
  
 Lorsque * \<type>* est le type de valeur que la classe anime.  
  
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
 Une animation From/To/By crée une transition entre deux valeurs cibles. Il est courant de spécifier une <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> valeur de départ (la définir <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> en utilisant la propriété) et une valeur de fin (la définir en utilisant la propriété). Toutefois, vous pouvez également spécifier uniquement une valeur de début, une valeur de destination ou une valeur de décalage. Dans ces cas, l’animation obtient la valeur cible manquante de la propriété qui est animée. La liste suivante décrit les différentes manières de spécifier les valeurs cibles d’une animation.  
  
- **Valeur de départ**  
  
     Utilisez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> la propriété lorsque vous souhaitez spécifier explicitement la valeur de départ d’une animation. Vous pouvez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> utiliser la propriété par <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> lui-même, ou avec le ou la propriété. Si vous ne <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> spécifiez que la propriété, l’animation passe de cette valeur à la valeur de base de la propriété animée.  
  
- **Valeur de fin**  
  
     Pour spécifier une valeur <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> de fin d’une animation, utilisez sa propriété. Si vous <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> utilisez la propriété par elle-même, l’animation obtient sa valeur de départ de la propriété qui est animée ou de la sortie d’une autre animation qui est appliquée à la même propriété. Vous pouvez <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> utiliser la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété avec la propriété pour spécifier explicitement les valeurs de démarrage et de fin pour l’animation.  
  
- **Valeur de décalage**  
  
     La <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété vous permet de spécifier un décalage au lieu d’une valeur de démarrage ou de fin explicite pour l’animation. La <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété d’une animation spécifie par la façon dont l’animation change une valeur sur sa durée. Vous pouvez <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> utiliser la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> par lui-même ou avec la propriété. Si vous ne <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> spécifiez que la propriété, l’animation ajoute la valeur offset à la valeur de base de la propriété ou à la sortie d’une autre animation.  
  
<a name="examples"></a>
## <a name="using-fromtoby-values"></a>Utilisation des valeurs From/To/By  
 Les sections suivantes décrivent <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>comment <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>utiliser <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> le , , et les propriétés ensemble ou séparément.  
  
 Les exemples dans cette <xref:System.Windows.Media.Animation.DoubleAnimation>section utilisent chacun un , qui est un type <xref:System.Windows.FrameworkElement.Width%2A> de <xref:System.Windows.Shapes.Rectangle> From / To / Par animation, pour animer la propriété d’un qui est de 10 pixels indépendants appareil haut et 100 pixels indépendants de périphérique de large.  
  
 Bien que chaque <xref:System.Windows.Media.Animation.DoubleAnimation>exemple utilise un , le From, To, et Par les propriétés de tous les From / To / Par animations se comportent de façon identique. Bien que chacun de <xref:System.Windows.Media.Animation.Storyboard>ces exemples utilise un , vous pouvez utiliser Des /To/ By animations d’autres façons. Pour plus d’informations, voir [Aperçu des techniques d’animation immobilière](property-animation-techniques-overview.md).  
  
### <a name="fromto"></a>De/À  
 Lorsque vous <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> définissez le et <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> les valeurs ensemble, l’animation progresse de la valeur qui est spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété, à la valeur qui est spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété.  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> donne <xref:System.Windows.Media.Animation.DoubleAnimation> à 300 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> la propriété des 50 et de sa propriété. En conséquence, <xref:System.Windows.FrameworkElement.Width%2A> le <xref:System.Windows.Shapes.Rectangle> de la est animée de 50 à 300.  
  
 [!code-csharp[basicvalues_snip#FromToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromtoanimationinline)]
 [!code-vb[basicvalues_snip#FromToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromtoanimationinline)]  
  
### <a name="to"></a>À  
 Lorsque vous définissez juste la <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété, l’animation progresse de la valeur de base de la propriété animée, ou de la sortie <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> d’une animation de composition qui a été précédemment appliquée à la même propriété, à la valeur qui est spécifiée par la propriété.  
  
 ("Composing animation" se <xref:System.Windows.Media.Animation.ClockState.Active> réfère <xref:System.Windows.Media.Animation.ClockState.Filling> à une ou une animation qui s’appliquait auparavant à <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> la même propriété qui est encore en vigueur lorsque l’animation actuelle a été appliquée en utilisant le comportement de transfert.)  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> ne définit <xref:System.Windows.Media.Animation.DoubleAnimation> que la propriété des 300. Étant donné qu’aucune <xref:System.Windows.Media.Animation.DoubleAnimation> valeur de départ n’a été <xref:System.Windows.FrameworkElement.Width%2A> spécifiée, la valeur de base (100) de la propriété est sa valeur de départ. Le <xref:System.Windows.FrameworkElement.Width%2A> de <xref:System.Windows.Shapes.Rectangle> la est animée de 100 à la valeur cible de l’animation de 300.  
  
 [!code-csharp[basicvalues_snip#ToAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#toanimationinline)]
 [!code-vb[basicvalues_snip#ToAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#toanimationinline)]  
  
### <a name="by"></a>par  
 Lorsque vous définissez juste la <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété d’une animation, l’animation progresse de la valeur de base de la propriété qui est animée, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> ou de la sortie d’une animation de composition à la somme de cette valeur et la valeur qui est spécifiée par la propriété.  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> ne définit <xref:System.Windows.Media.Animation.DoubleAnimation> que la propriété des 300. Étant donné que l’exemple ne <xref:System.Windows.Media.Animation.DoubleAnimation> précise pas de <xref:System.Windows.FrameworkElement.Width%2A> valeur de départ, la valeur de base de la propriété, 100, comme valeur de départ. La valeur de fin <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> est déterminée en ajoutant la valeur de l’animation, 300, à sa valeur de départ, 100: 400. En conséquence, <xref:System.Windows.FrameworkElement.Width%2A> le <xref:System.Windows.Shapes.Rectangle> de la est animée de 100 à 400.  
  
 [!code-csharp[basicvalues_snip#ByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#byanimationinline)]
 [!code-vb[basicvalues_snip#ByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#byanimationinline)]  
  
### <a name="fromby"></a>From/By  
 Lorsque vous <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> définissez les <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriétés et les propriétés d’une <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> animation, l’animation progresse de la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> valeur spécifiée par la propriété, à la valeur qui est spécifiée par la somme de la et des propriétés.  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> donne <xref:System.Windows.Media.Animation.DoubleAnimation> à 300 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> la propriété des 50 et de sa propriété. La valeur de fin <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> est déterminée en ajoutant la valeur de l’animation, 300, à sa valeur de départ, 50: 350. En conséquence, <xref:System.Windows.FrameworkElement.Width%2A> le <xref:System.Windows.Shapes.Rectangle> de la est animée de 50 à 350.  
  
 [!code-csharp[basicvalues_snip#FromByAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#frombyanimationinline)]
 [!code-vb[basicvalues_snip#FromByAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#frombyanimationinline)]  
  
### <a name="from"></a>À partir  
 Lorsque vous spécifiez juste la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> valeur d’une animation, <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> l’animation progresse de la valeur qui est spécifiée par la propriété, à la valeur de base de la propriété qui est animée ou à la sortie d’une animation de composition.  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> ne définit <xref:System.Windows.Media.Animation.DoubleAnimation> que la propriété des 50. Étant donné qu’aucune <xref:System.Windows.Media.Animation.DoubleAnimation> valeur finale n’a été spécifiée, la valeur de base de la <xref:System.Windows.FrameworkElement.Width%2A> propriété 100, comme valeur finale. Le <xref:System.Windows.FrameworkElement.Width%2A> de <xref:System.Windows.Shapes.Rectangle> la est animée de 50 <xref:System.Windows.FrameworkElement.Width%2A> à la valeur de base de la propriété, 100.  
  
 [!code-csharp[basicvalues_snip#FromAnimationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/basicvalues_snip/CSharp/AnimationTargetValuesExample.cs#fromanimationinline)]
 [!code-vb[basicvalues_snip#FromAnimationInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/basicvalues_snip/VisualBasic/AnimationTargetValuesExample.vb#fromanimationinline)]  
  
### <a name="toby"></a>To/By  
 Si vous définissez à la fois les <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriétés et les <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriétés d’une animation, la <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> propriété est ignorée.  
  
<a name="otheranimationtypes"></a>
## <a name="other-animation-types"></a>Autres types d’animations  
 De/To/By animations ne sont pas le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] seul type d’animations qui fournit: il fournit également des animations à cadre clé et des animations de chemin.  
  
- Une animation d’image clé est animée avec n’importe quel nombre de valeurs de destination et décrite à l’aide d’images clés. Pour plus d’informations, consultez le [Aperçu des animations Key-Frame](key-frame-animations-overview.md).  
  
- Une animation de chemin génère <xref:System.Windows.Media.PathGeometry>des valeurs de sortie à partir d’un . Pour plus d’informations, voir le [Path Animations Overview](path-animations-overview.md).  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet également de créer vos propres types d’animations personnalisées. Pour plus d’informations, consultez le [Aperçu des animations personnalisées](custom-animations-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des plans conceptuels](storyboards-overview.md)
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Vue d'ensemble des animations de tracés](path-animations-overview.md)
- [Vue d'ensemble des animations personnalisées](custom-animations-overview.md)
- [Exemple de valeurs cibles d’animation From, To et By](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
