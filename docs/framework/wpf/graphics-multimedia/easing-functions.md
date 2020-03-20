---
title: Fonctions d'accélération
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
ms.openlocfilehash: a25bde5098af853c3906a174a189fc35f33f0525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186498"
---
# <a name="easing-functions"></a>Fonctions d'accélération
Les fonctions d’accélération permettent d’appliquer des formules mathématiques personnalisées à des animations. Par exemple, vous pouvez faire en sorte qu’un objet rebondisse ou se comporte comme s’il était sur un ressort de façon réaliste. On peut utiliser des animations d’images clés ou même From/To/By pour se rapprocher de ces effets, mais cela demanderait beaucoup de travail et l’animation serait moins précise qu’avec une formule mathématique.  
  
 En plus de créer votre propre <xref:System.Windows.Media.Animation.EasingFunctionBase>fonction d’assouplissement personnalisé en héritant de , vous pouvez utiliser l’une des nombreuses fonctions d’assouplissement fournis par le temps d’exécution pour créer des effets communs.  
  
- <xref:System.Windows.Media.Animation.BackEase>: Rétracte légèrement le mouvement d’une animation avant de commencer à animer le chemin indiqué.  
  
- <xref:System.Windows.Media.Animation.BounceEase>: Crée un effet rebondissant.  
  
- <xref:System.Windows.Media.Animation.CircleEase>: Crée une animation qui accélère et/ou décélère à l’aide d’une fonction circulaire.  
  
- <xref:System.Windows.Media.Animation.CubicEase>: Crée une animation qui accélère et/ou décélère à l’aide de la formule *f*(*t*) *t*<sup>3</sup>.  
  
- <xref:System.Windows.Media.Animation.ElasticEase>: Crée une animation qui ressemble à un printemps oscillant d’avant en arrière jusqu’à ce qu’il se repose.  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>: Crée une animation qui accélère et/ou décélère à l’aide d’une formule exponentielle.  
  
- <xref:System.Windows.Media.Animation.PowerEase>: Crée une animation qui accélère et/ou décélère à l’aide de la <xref:System.Windows.Media.Animation.PowerEase.Power%2A> formule *f**(t)* *t*<sup>p</sup> où p est égal à la propriété.  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>: Crée une animation qui accélère et/ou décélère à l’aide de la formule *f*(*t*) *t*<sup>2</sup>.  
  
- <xref:System.Windows.Media.Animation.QuarticEase>: Crée une animation qui accélère et/ou décélère à l’aide de la formule *f*(*t*) *t*<sup>4</sup>.  
  
- <xref:System.Windows.Media.Animation.QuinticEase>: Créer une animation qui accélère et/ou décélère à l’aide de la formule *f*(*t*) *t*<sup>5</sup>.  
  
- <xref:System.Windows.Media.Animation.SineEase>: Crée une animation qui accélère et/ou décélère à l’aide d’une formule sinusoïdienne.  
  
 Pour appliquer une fonction d’assouplissement `EasingFunction` à une animation, utilisez la propriété de l’animation spécifier la fonction d’assouplissement à appliquer à l’animation. L’exemple suivant <xref:System.Windows.Media.Animation.BounceEase> applique une <xref:System.Windows.Media.Animation.DoubleAnimation> fonction d’assouplissement à un pour créer un effet rebondissant.  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 Dans l’exemple précédent, la fonction d’accélération a été appliquée à une animation From/To/By. Vous pouvez également appliquer ces fonctions d’accélération aux animations d’images clés. L’exemple suivant montre comment utiliser des images clés avec les fonctions d’accélération associées pour créer une animation d’un rectangle qui se contracte vers le haut, ralentit, s’étend vers le bas (comme s’il tombait), puis rebondit jusqu’à s’arrêter.  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Vous pouvez <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> utiliser la propriété pour modifier la façon dont la fonction d’assouplissement se comporte, c’est-à-dire changer la façon dont l’animation interpole. Il y a trois valeurs <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>possibles que vous pouvez donner pour :  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: L’interpolation suit la formule mathématique associée à la fonction d’assouplissement.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation suit 100% d’interpolation moins la sortie de la formule associée à la fonction d’assouplissement.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation <xref:System.Windows.Media.Animation.EasingMode.EaseIn> utilise pour la première <xref:System.Windows.Media.Animation.EasingMode.EaseOut> moitié de l’animation et pour la seconde moitié.  
  
 Les graphiques ci-dessous <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> démontrent les différentes valeurs de l’endroit où *f*(*x*) représente le progrès de l’animation et *t* représente le temps.  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![Graphiques EasingMode BackEase.](./media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![Graphiques EasingMode BounceEase.](./media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![Graphiques EasingMode CircleEase.](./media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![Graphiques EasingMode CubicEase.](./media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![ElasticEase avec graphiques de différents easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![Graphiques ExponentialEase de différents easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![QuarticEase avec graphiques de différents easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![QuadraticEase avec graphiques de différents easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![QuarticEase avec graphiques de différents easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![QuinticEase avec graphiques de différents easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![SineEase pour différentes valeurs EasingMode](./media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
> Vous pouvez <xref:System.Windows.Media.Animation.PowerEase> utiliser pour créer <xref:System.Windows.Media.Animation.CubicEase> <xref:System.Windows.Media.Animation.QuadraticEase>le <xref:System.Windows.Media.Animation.QuarticEase>même <xref:System.Windows.Media.Animation.QuinticEase> comportement <xref:System.Windows.Media.Animation.PowerEase.Power%2A> que , , , et en utilisant la propriété. Par exemple, si vous <xref:System.Windows.Media.Animation.PowerEase> souhaitez <xref:System.Windows.Media.Animation.CubicEase>utiliser pour <xref:System.Windows.Media.Animation.PowerEase.Power%2A> remplacer , spécifiez une valeur de 3.  
  
 En plus d’utiliser les fonctions d’assouplissement incluses dans le temps d’exécution, vous pouvez créer vos propres fonctions d’assouplissement personnalisé en héritant de <xref:System.Windows.Media.Animation.EasingFunctionBase>. L’exemple suivant montre comment créer une fonction d’accélération personnalisée simple. Vous pouvez ajouter votre propre logique mathématique pour la façon <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> dont la fonction d’assouplissement se comporte en l’emporteant sur la méthode.
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
