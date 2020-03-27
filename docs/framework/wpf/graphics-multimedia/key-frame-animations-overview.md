---
title: Vue d'ensemble des animations d'image clé
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
ms.openlocfilehash: 8eb590b07eae3b76b3a206b9731997a6bc2c90d7
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344908"
---
# <a name="key-frame-animations-overview"></a>Vue d'ensemble des animations d'image clé
Cette rubrique présente les animations d’image clé. Les animations d’image clé vous permettent d’effectuer des animation en utilisant plus de deux valeurs cibles et de contrôler la méthode d’interpolation d’une animation.  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>Prérequis  
 Pour comprendre cette vue d’ensemble, vous devez être familiarisé avec les animations et les chronologies de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Pour une introduction aux animations, consultez [Vue d’ensemble de l’animation](animation-overview.md). Cette rubrique vous permet également de vous familiariser avec les animations From/To/By. Pour plus d’informations, consultez la Vue d’ensemble des animations From/To/By.  
  
<a name="whatisakeyframeanimation"></a>
## <a name="what-is-a-key-frame-animation"></a>Qu’est-ce qu’une animation d’image clé ?  
 Comme une animation From/To/By, une animation d’image clé anime la valeur d’une propriété cible. Il crée une transition entre <xref:System.Windows.Media.Animation.Timeline.Duration%2A>ses valeurs cibles sur son . Toutefois, contrairement à une animation From/To/By qui crée une transition entre deux valeurs, une animation d’image clé unique peut créer des transitions parmi n’importe quel nombre de valeurs cibles. Contrairement à une animation From/To/By, une animation d’image clé n’a aucune propriété From, To ou By avec lesquelles définir ses valeurs cibles. Les valeurs cibles d’une animation d’image clé sont décrites à l’aide d’objets d’images clés (d’où le terme « animation d’image clé »). Pour spécifier les valeurs cibles de l’animation, vous <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> créez des objets de cadre clés et les ajoutez à la collection de l’animation. Lorsque l’animation s’exécute, elle effectue la transition entre les images que vous avez spécifiées.  
  
 Outre la prise en charge de plusieurs valeurs cibles, certaines méthodes d’image clé prennent même en charge plusieurs méthodes d’interpolation. La méthode d’interpolation d’une animation définit la manière dont elle passe d’une valeur à l’autre. Il existe trois types d’interpolations : discrète, linéaire et spline.  
  
 Pour utiliser une animation d’image clé, procédez comme suit.  
  
- Déclarez l’animation <xref:System.Windows.Media.Animation.Timeline.Duration%2A>et spécifier son , tout comme vous le feriez pour un de / à / par animation.  
  
- Pour chaque valeur cible, créez un cadre clé du <xref:System.Windows.Media.Animation.KeyTime>type approprié, définissez <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> sa valeur et, et ajoutez-la à la collection de l’animation.  
  
- Associez l’animation à une propriété, comme vous le feriez avec une animation From/To/By. Pour plus d’informations sur l’application d’une animation à une propriété à l’aide d’une table de montage séquentiel, consultez la [Vue d’ensemble des storyboards](storyboards-overview.md).  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> utilise un <xref:System.Windows.Shapes.Rectangle> élément pour animer quatre endroits différents.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 Comme une animation From/To/By, une animation à cadre clé <xref:System.Windows.Media.Animation.Storyboard> peut être appliquée à une <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> propriété en utilisant un balisage et un code ou en utilisant la méthode dans le code. Vous pouvez également utiliser une animation <xref:System.Windows.Media.Animation.AnimationClock> à cadre clé pour créer un et l’appliquer à une ou plusieurs propriétés. Pour plus d’informations sur les différentes méthodes d’application des animations, voir le [Aperçu des techniques d’animation de](property-animation-techniques-overview.md)propriété .  
  
<a name="animation_types"></a>
## <a name="key-frame-animation-types"></a>Types d’animations d’image clé  
 Étant donné que les animations génèrent des valeurs de propriété, il existe différents types d’animation pour différents types de propriété. Pour animer une propriété <xref:System.Double> qui prend une propriété <xref:System.Windows.FrameworkElement.Width%2A> (comme la propriété <xref:System.Double> d’un élément), vous utilisez une animation qui produit des valeurs. Pour animer une propriété <xref:System.Windows.Point>qui prend un , <xref:System.Windows.Point> vous utilisez une animation qui produit des valeurs, et ainsi de suite.  
  
 Les classes d’animation à <xref:System.Windows.Media.Animation> cadre clé appartiennent à l’espace de nom et adhèrent à la convention de nommage suivante :  
  
 * \<Type>*`AnimationUsingKeyFrames`  
  
 Lorsque * \<type>* est le type de valeur que la classe anime.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit les classes d’animation d’image clé suivantes.  
  
|Type de propriété|Animation From/To/By correspondante|Méthodes d’interpolation prises en charge|  
|-------------------|------------------------------------------------|-------------------------------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|Discret|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|Discret|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|Discret|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|Discret|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|Discrète, linéaire, spline|  
  
<a name="animation_target_values"></a>
## <a name="target-values-key-frames-and-key-times"></a>Valeurs cibles (images clés) et temps clés  
 Tout comme il existe différents types d’animations d’image clé pour animer différents types de propriété, il existe également différents types d’objets d’image clé : un pour chaque type de valeur animée et pour chaque méthode d’interpolation prise en charge. Les types d’image clé obéissent à la convention d’affectation de noms suivante :  
  
 *InterpolationMethod>\<Type>\<*`KeyFrame`  
  
 Là où * \<InterpolationMethod>* est la méthode * \<* d’interpolation que le cadre clé utilise et tape>est le type de valeur que la classe anime. Une animation d’image clé qui prend en charge les trois méthodes d’interpolation aura trois types d’image clé que vous pouvez utiliser. Par exemple, vous pouvez utiliser trois <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>types <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>de <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>cadre clé avec un : , , et . (Les méthodes d’interpolation sont décrites en détail dans une section ultérieure.)  
  
 Le but principal d’un cadre <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> clé <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>est de spécifier un et un . Chaque type d’image clé fournit ces deux propriétés.  
  
- La <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> propriété spécifie la valeur cible de ce cadre clé.  
  
- La <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> propriété spécifie lorsque <xref:System.Windows.Media.Animation.Timeline.Duration%2A>(dans l’animation) un cadre clé <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> est atteint.  
  
 Lorsqu’une animation de cadre clé commence, itère à travers <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> ses cadres clés dans l’ordre défini par leurs propriétés.  
  
- S’il n’y a pas de cadre clé au moment 0, <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> l’animation crée une transition entre la valeur actuelle de la propriété cible et le cadre de la première clé; sinon, la valeur de sortie de l’animation devient la valeur du premier cadre clé.  
  
- L’animation crée une <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> transition entre les cadres de la première et du deuxième clé en utilisant la méthode d’interpolation spécifiée par le deuxième cadre clé. La transition commence à la <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> première image clé et se <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> termine lorsque le deuxième cadre clé est atteint.  
  
- L’animation continue, en créant des transitions entre chaque image clé suivante et son image clé précédente.  
  
- Enfin, l’animation passe à la valeur du cadre clé avec le plus grand <xref:System.Windows.Media.Animation.Timeline.Duration%2A>temps clé qui est égal ou plus petit que l’animation .  
  
 Si l’animation <xref:System.Windows.Media.Animation.Timeline.Duration%2A> <xref:System.Windows.Duration.Automatic%2A> est <xref:System.Windows.Media.Animation.Timeline.Duration%2A> ou son est égal à l’heure du dernier cadre clé, l’animation se termine. Sinon, si l’animation est supérieure à l’heure <xref:System.Windows.Duration> clé du dernier cadre clé, l’animation <xref:System.Windows.Duration>détient la valeur du cadre clé jusqu’à ce qu’elle atteigne la fin de son . Comme toutes les animations, une <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> animation à cadre clé utilise sa propriété pour déterminer si elle lui détient la valeur finale lorsqu’elle atteint la fin de sa période active. Pour plus d’informations, consultez l’article [Vue d’ensemble des comportements de minutage](timing-behaviors-overview.md).  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> utilise l’objet défini dans <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> l’exemple précédent pour démontrer comment les propriétés et les propriétés fonctionnent.  
  
- La première image clé affecte immédiatement la valeur de sortie de l’animation à 0.  
  
- La deuxième image clé s’anime de 0 à 350. Elle démarre après la fin de la première image clé (au temps = 0 seconde) et est lue pendant 2 secondes, pour se terminer au temps = 0:0:2.  
  
- La troisième image clé s’anime de 350 à 50. Elle démarre après la fin de la deuxième image clé (au temps = 2 secondes) et est lue pendant 5 secondes, pour se terminer au temps = 0:0:7.  
  
- La quatrième image clé s’anime de 50 à 200. Elle démarre après la fin de la troisième image clé (au temps = 7 secondes) et est lue pendant 1 seconde, pour se terminer au temps = 0:0:8.  
  
- Parce <xref:System.Windows.Media.Animation.Timeline.Duration%2A> que la propriété de l’animation a été réglée à 10 secondes, l’animation détient sa valeur finale pendant deux secondes avant de se terminer à l’heure à 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>
## <a name="interpolation-methods"></a>Méthodes d’interpolation  
 Nous avons vu dans les sections précédentes que certaines animations d’image clé prennent en charge plusieurs méthodes d’interpolation. L’interpolation d’une animation décrit la manière une animation transite entre les valeurs sur sa durée. En sélectionnant le type d’image clé que vous utilisez avec votre animation, vous pouvez définir la méthode d’interpolation correspondant à ce segment d’image clé. Il existe trois types de méthodes d’interpolation : linéaire, discrète et spline.  
  
### <a name="linear-interpolation"></a>Interpolation linéaire  
 Avec l’interpolation linéaire, l’animation progresse à une vitesse constante pendant la durée du segment. Par exemple, si un segment d’image clé passe de 0 à 10 sur une durée de 5 secondes, l’animation générera les valeurs suivantes aux temps spécifiés :  
  
|Temps|Valeur de sortie|  
|----------|------------------|  
|0|0|  
|1|2|  
|2|4|  
|3|6|  
|4|8|  
|4.25|8.5|  
|4.5|9|  
|5|10|  
  
### <a name="discrete-interpolation"></a>Interpolation discrète  
 Avec l’interpolation discrète, la fonction d’animation passe d’une valeur à la suivante sans interpolation. Si un segment d’image clé passe de 0 à 10 sur une durée de 5 secondes, l’animation générera les valeurs suivantes aux temps spécifiés :  
  
|Temps|Valeur de sortie|  
|----------|------------------|  
|0|0|  
|1|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4.5|0|  
|5|10|  
  
 Notez que l’animation ne change pas sa valeur de sortie avant la fin de la durée du segment.  
  
 L’interpolation spline est plus complexe. Elle est décrite dans la section suivante.  
  
<a name="anim_spline"></a>
### <a name="splined-interpolation"></a>Interpolation spline  
 L’interpolation spline peut être utilisée pour obtenir des effets de minutage plus réalistes. Étant donné que les animations sont souvent utilisées pour imiter des effets qui se produisent dans le monde réel, les développeurs peuvent avoir à contrôler précisément l’accélération et la décélération des objets, et devoir manipuler précisément les segments de minutage. Les images clés spline vous permettent d’effectuer des animation avec une interpolation spline. Avec d’autres cadres clés, vous spécifiez un <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> et <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>. Avec un cadre de clé spline, vous spécifiez également un <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>. L’exemple suivant montre un cadre <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>clé spline unique pour un . Remarquez <xref:System.Windows.Media.Animation.KeySpline> la propriété; c’est ce qui rend un cadre clé spline différent des autres types de cadres clés.  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Une courbe de Bézier cubique est définie par un point de départ, un point de terminaison et deux points de contrôle. La <xref:System.Windows.Media.Animation.KeySpline> propriété d’un cadre de clé spline définit les deux points de contrôle d’une courbe bézier qui s’étend de (0,0) à (1,1). Le premier point de contrôle permet de contrôler le facteur de courbe de la première moitié de la courbe de Bézier ; le deuxième point de contrôle permet de contrôler le facteur de courbe de la seconde moitié de la courbe de Bézier. La courbe obtenue décrit la vitesse de changement pour cette image clé spline. Plus la courbe est raide, plus vite l’image clé modifie ses valeurs. À mesure que la courbe s’aplatit, l’image clé modifie ses valeurs plus lentement.  
  
 Vous pouvez <xref:System.Windows.Media.Animation.KeySpline> utiliser pour simuler des trajectoires physiques comme la chute d’eau ou des boules rebondissantes, ou appliquer d’autres "facilité" et "faciliter" les effets sur les animations de mouvement. Pour les effets d’interaction utilisateur comme les atténuations d’arrière-plan ou le rebond du bouton de contrôle, vous pouvez appliquer l’interpolation spline pour accélérer ou ralentir la vitesse de changement d’une animation d’une façon spécifique.  
  
 L’exemple suivant spécifie un <xref:System.Windows.Media.Animation.KeySpline> de 0,1 1,0, ce qui crée la courbe suivante de Bézier.  
  
 ![Courbe de Bézier](./media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
Courbe clé avec les points de contrôle (0.0, 1.0) et (1.0, 0.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 Cette image clé s’anime rapidement lorsqu’elle commence, puis ralentit et accélère à nouveau avant de se terminer.  
  
 L’exemple suivant spécifie une <xref:System.Windows.Media.Animation.KeySpline> courbe de 0,5,0,25 0,75,1,0, ce qui crée la courbe suivante de Bézier.  
  
 ![Courbe de Bézier](./media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
Courbe clé avec les points de contrôle (0.25, 0.5) et (0.75, 1.0)  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 Étant donné que la courbure de la courbe de Bézier change très peu, cette image clé s’anime à une fréquence presque constante ; elle ralentit quelque peu vers la fin.  
  
 L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> utilise un pour animer la position du rectangle. Parce <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> que <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> l’utilisation d’objets, la transition entre chaque valeur de cadre clé utilise l’interpolation splined.  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 L’interpolation spline peut être difficile à comprendre ; il peut être utile d’expérimenter différents paramètres. [L’exemple d’animation de courbe clé](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations) vous permet de modifier les valeurs de courbe clé et de voir son résultat dans une animation.  
  
<a name="combininginterpolationmethods"></a>
### <a name="combining-interpolation-methods"></a>Combinaison de méthodes d’interpolation  
 Vous pouvez utiliser des images clés avec différents types d’interpolation dans une animation d’image clé unique. Lorsque deux animations d’image clé avec des interpolations différentes se suivent, la méthode d’interpolation de la deuxième image clé est utilisée pour créer la transition entre la première valeur et la seconde.  
  
 Dans l’exemple <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> suivant, un est créé qui utilise une interpolation linéaire, splined, et discrète.  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>
## <a name="more-about-duration-and-key-times"></a>En savoir plus sur la durée et les temps clés  
 Comme d’autres animations, les <xref:System.Windows.Duration> animations à cadre clé ont une propriété. En plus de spécifier l’animation, <xref:System.Windows.Duration>vous devez spécifier quelle partie de cette durée est donnée à chaque cadre clé. Vous le faites <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> en décrivant un pour chacun des cadres clés de l’animation. Chaque cadre de <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> clé spécifie lorsque ce cadre clé se termine.  
  
 La <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> propriété ne précise pas combien de temps le temps clé joue. La durée de lecture d’une image clé est déterminée par le moment où l’image clé se termine, par le moment où l’image clé précédente a pris fin et par la durée de l’animation. Les temps clés peuvent être spécifiés comme une valeur <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>temporelle, un pourcentage, ou comme les valeurs spéciales ou .  
  
 La liste suivante décrit les différentes façons de spécifier des temps clés.  
  
### <a name="timespan-values"></a>Valeurs TimeSpan  
 Vous pouvez <xref:System.TimeSpan> utiliser des <xref:System.Windows.Media.Animation.KeyTime>valeurs pour spécifier un . La valeur doit être supérieure ou égale à 0 et inférieure ou égale à la durée de l’animation. L’exemple suivant illustre une animation d’une durée de 10 secondes qui comporte quatre images clés dont les temps clés sont spécifiés en tant que valeurs de temps.  
  
- La première image clé s’anime entre la valeur de base et 100 pendant les 3 premières secondes, et se termine au temps = 0:0:03.  
  
- La deuxième image clé s’anime de 100 à 200. Elle démarre après la fin de la première image clé (au temps = 3 secondes) et est lue pendant 5 secondes, pour se terminer au temps = 0:0:8.  
  
- La troisième image clé s’anime de 200 à 500. Elle démarre après la fin de la deuxième image clé (au temps = 8 secondes) et est lue pendant 1 seconde, pour se terminer au temps = 0:0:9.  
  
- La quatrième image clé s’anime de 500 à 600. Elle démarre après la fin de la troisième image clé (au temps = 9 secondes) et est lue pendant 1 seconde, pour se terminer au temps = 0:0:10.  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>Valeurs de pourcentage  
 Une valeur en pourcentage spécifie que le cadre <xref:System.Windows.Media.Animation.Timeline.Duration%2A>clé se termine à un certain pourcentage de l’animation . Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous spécifiez le pourcentage sous la forme d’un nombre suivi par le symbole `%`. Dans le code, <xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> vous utilisez la <xref:System.Double> méthode et la transmettez un indiquant le pourcentage. La valeur doit être supérieure ou égale à 0 et inférieure ou égale à 100 %. L’exemple suivant illustre une animation d’une durée de 10 secondes qui comporte quatre images clés dont les temps clés sont spécifiés en tant que pourcentages.  
  
- La première image clé s’anime entre la valeur de base et 100 pendant les 3 premières secondes, et se termine au temps = 0:0:3.  
  
- La deuxième image clé s’anime de 100 à 200. Elle démarre après la fin de la première image clé (au temps = 3 secondes) et est lue pendant 5 secondes, pour se terminer au temps = 0:0:8 (0.8 * 10 = 8).  
  
- La troisième image clé s’anime de 200 à 500. Elle démarre après la fin de la deuxième image clé (au temps = 8 secondes) et est lue pendant 1 seconde, pour se terminer au temps = 0:0:9 (0.9 * 10 = 9).  
  
- La quatrième image clé s’anime de 500 à 600. Elle démarre après la fin de la troisième image clé (au temps = 9 secondes) et est lue pendant 1 seconde, pour se terminer au temps = 0:0:10 (1 * 10 = 10).  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>Valeur spéciale, Uniform  
 Utilisez <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> le moment lorsque vous voulez que chaque cadre clé prenne le même temps.  
  
 Un <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> temps clé divise le temps disponible également par le nombre d’images clés pour déterminer l’heure de fin de chaque cadre clé. L’exemple suivant montre une animation d’une durée de 10 secondes <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>et quatre cadres clés dont les temps clés sont spécifiés comme .  
  
- La première image clé s’anime entre la valeur de base et 100 pendant les 2,5 premières secondes, et se termine au temps = 0:0:2.5.  
  
- La deuxième image clé s’anime de 100 à 200. Elle démarre après la fin de la première image clé (au temps = 2,5 secondes) et est lue pendant environ 2,5 secondes, pour se terminer au temps = 0:0:5.  
  
- La troisième image clé s’anime de 200 à 500. Elle démarre après la fin de la deuxième image clé (au temps = 5 secondes) et est lue pendant 2,5 secondes, pour se terminer au temps = 0:0:7.5.  
  
- La quatrième image clé s’anime de 500 à 600. Elle démarre après la fin de la deuxième image clé (au temps = 7,5 secondes) et est lue pendant 2,5 secondes, pour se terminer au temps = 0:0:1.  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>Valeur spéciale, Paced  
 Utilisez <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> le moment lorsque vous voulez animer à un rythme constant.  
  
 Un <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> temps clé alloue le temps disponible en fonction de la longueur de chacun des cadres clés pour déterminer la durée de chaque image.  Cela permet de maintenir constante la vitesse ou la fréquence de l’animation.  L’exemple suivant montre une animation d’une durée de 10 secondes <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>et trois cadres clés dont les temps clés sont spécifiés comme .  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 Notez que, si l’heure clé <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>du dernier cadre clé est ou, son temps clé résolu sera réglé à 100 pour cent. Si la première image clé dans une animation à plusieurs images est rythmée, son temps clé résolu est défini sur 0. (Si la collection d’images clé contient seulement une image clé unique et s’il s’agit d’une image clé rythmée, son temps clé résolu aura une valeur de 100 %.)  
  
 Les différentes images clés d’une même animation d’image clé peuvent utiliser des temps clés différents.  
  
<a name="combiningkeytimes"></a>
## <a name="combining-key-times-out-of-order-key-frames"></a>Combinaison de temps clés avec des images clés dans le désordre  
 Vous pouvez utiliser des <xref:System.Windows.Media.Animation.KeyTime> cadres clés avec différents types de valeur dans la même animation. Et, bien qu’il soit recommandé d’ajouter des images clés dans l’ordre dans lequel elles doivent être lues, cela n’est pas forcément nécessaire. Le système d’animation et de minutage est capable de résoudre des images clés désordonnées. Les images clés avec des temps clés non valides sont ignorées.  
  
 La section suivante décrit la procédure qui permet de résoudre les temps clés pour les images clés d’une animation d’image clé.  
  
1. Résoudre <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> les valeurs.  
  
2. Déterminez le *temps total d’interpolation* de l’animation, c’est-à-dire la durée totale nécessaire à l’animation d’image clé pour exécuter une itération avancée.  
  
    1. Si l’animation <xref:System.Windows.Media.Animation.Timeline.Duration%2A> n’est pas <xref:System.Windows.Duration.Automatic%2A> ou, <xref:System.Windows.Duration.Forever%2A>le temps d’interpolation total est la valeur de la propriété de <xref:System.Windows.Media.Animation.Timeline.Duration%2A> l’animation.  
  
    2. Dans le cas contraire, le <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> temps total d’interpolation est la valeur la plus importante spécifiée parmi ses cadres clés, le cas échéant.  
  
    3. Sinon, le temps total d’interpolation est de 1 seconde.  
  
3. Utilisez la valeur totale du <xref:System.Windows.Media.Animation.KeyTimeType.Percent> <xref:System.Windows.Media.Animation.KeyTime> temps d’interpolation pour résoudre les valeurs.  
  
4. Résolvez la dernière image clé, si elle n’a pas déjà été résolue dans les étapes précédentes. Si <xref:System.Windows.Media.Animation.KeyTime> le dernier cadre <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> clé <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>est ou, son temps résolu sera égal au temps total d’interpolation.  
  
     Si <xref:System.Windows.Media.Animation.KeyTime> le cadre de <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> la première clé est et cette animation <xref:System.Windows.Media.Animation.KeyTime> a plus que sur les cadres clés, résoudre sa valeur à zéro; s’il n’y a <xref:System.Windows.Media.Animation.KeyTime> qu’un seul cadre clé et que sa valeur est, <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>elle est résolue au temps total d’interpolation, tel que décrit dans l’étape précédente.  
  
5. Résoudre <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> les valeurs restantes : elles reçoivent chacune une part égale du temps disponible.  Au cours de <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> ce processus, les <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> valeurs non résolues sont temporairement traitées comme des valeurs et obtiennent un délai temporaire résolu.  
  
6. Résoudre <xref:System.Windows.Media.Animation.KeyTime> les valeurs des cadres clés avec des temps clés non spécifiés en <xref:System.Windows.Media.Animation.KeyTime> utilisant les cadres clés déclarés les plus proches qui ont résolu les valeurs.  
  
7. Résoudre <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> les valeurs restantes. <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime> utiliser <xref:System.Windows.Media.Animation.KeyTime> les valeurs des cadres clés voisins pour déterminer leur temps de résolution.  L’objectif est de vous assurer que la vitesse de l’animation reste constante autour du temps résolu de cette image clé.  
  
8. Trier les cadres clés par ordre de temps résolu (clé primaire) et l’ordre de déclaration (clé <xref:System.Windows.Media.Animation.KeyTime> secondaire), c’est-à-dire utiliser un type stable basé sur les valeurs de cadre clés résolues.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.KeyTime>
- <xref:System.Windows.Media.Animation.KeySpline>
- <xref:System.Windows.Media.Animation.Timeline>
- [Animation de spline clé, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/KeySplineAnimations)
- [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)
- [Vue d'ensemble de l'animation](animation-overview.md)
- [Vue d'ensemble des storyboards](storyboards-overview.md)
- [Guides pratiques relatifs aux images clés](key-frame-animation-how-to-topics.md)
- [Vue d'ensemble des comportements de minutage](timing-behaviors-overview.md)
