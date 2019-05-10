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
ms.openlocfilehash: a74142b8d8ee3a68daa9966e3f20f3b8e3becb72
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615400"
---
# <a name="easing-functions"></a>Fonctions d'accélération
Les fonctions d’accélération permettent d’appliquer des formules mathématiques personnalisées à des animations. Par exemple, vous pouvez faire en sorte qu’un objet rebondisse ou se comporte comme s’il était sur un ressort de façon réaliste. On peut utiliser des animations d’images clés ou même From/To/By pour se rapprocher de ces effets, mais cela demanderait beaucoup de travail et l’animation serait moins précise qu’avec une formule mathématique.  
  
 Outre la création de votre propre fonction d’accélération personnalisée en héritant de <xref:System.Windows.Media.Animation.EasingFunctionBase>, vous pouvez utiliser une des fonctions d’accélération fournies par le runtime pour créer des effets courants.  
  
- <xref:System.Windows.Media.Animation.BackEase>: Rétracte légèrement le mouvement d’une animation avant qu’elle ne commence dans le chemin d’accès indiqué.  
  
- <xref:System.Windows.Media.Animation.BounceEase>: Crée un effet rebondissant.  
  
- <xref:System.Windows.Media.Animation.CircleEase>: Crée une animation qui accélère et/ou ralentit en utilisant une fonction circulaire.  
  
- <xref:System.Windows.Media.Animation.CubicEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>3</sup>.  
  
- <xref:System.Windows.Media.Animation.ElasticEase>: Crée une animation qui ressemble à un ressort OSCILLANT jusqu'à ce qu’il s’agit de rest.  
  
- <xref:System.Windows.Media.Animation.ExponentialEase>: Crée une animation qui accélère et/ou ralentit en utilisant une formule exponentielle.  
  
- <xref:System.Windows.Media.Animation.PowerEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>p</sup> où p est égal à la <xref:System.Windows.Media.Animation.PowerEase.Power%2A>propriété.  
  
- <xref:System.Windows.Media.Animation.QuadraticEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>2</sup>.  
  
- <xref:System.Windows.Media.Animation.QuarticEase>: Crée une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>4</sup>.  
  
- <xref:System.Windows.Media.Animation.QuinticEase>: Créer une animation qui accélère et/ou ralentit à l’aide de la formule *f*(*t*) = *t*<sup>5</sup>.  
  
- <xref:System.Windows.Media.Animation.SineEase>: Crée une animation qui accélère et/ou ralentit en utilisant une formule de sinus.  
  
 Pour appliquer une fonction d’accélération à une animation, utilisez le `EasingFunction` propriété de l’animation spécifier la fonction d’accélération à appliquer à l’animation. L’exemple suivant applique un <xref:System.Windows.Media.Animation.BounceEase> fonction d’accélération un <xref:System.Windows.Media.Animation.DoubleAnimation> pour créer un effet rebondissant.  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 Dans l’exemple précédent, la fonction d’accélération a été appliquée à une animation From/To/By. Vous pouvez également appliquer ces fonctions d’accélération aux animations d’images clés. L’exemple suivant montre comment utiliser des images clés avec les fonctions d’accélération associées pour créer une animation d’un rectangle qui se contracte vers le haut, ralentit, s’étend vers le bas (comme s’il tombait), puis rebondit jusqu’à s’arrêter.  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 Vous pouvez utiliser le <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> propriété pour modifier la façon dont la fonction d’accélération se comporte, autrement dit, modifier le mode d’interpolation de l’animation. Il existe trois valeurs possibles, vous pouvez donner de <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: L’interpolation suit la formule mathématique associée à la fonction d’accélération.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: L’interpolation suit 100 % d’interpolation moins la sortie de la formule associée à la fonction d’accélération.  
  
- <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: L’interpolation utilise <xref:System.Windows.Media.Animation.EasingMode.EaseIn> pour la première moitié de l’animation et <xref:System.Windows.Media.Animation.EasingMode.EaseOut> lors de la seconde.  
  
 Les graphiques suivants montrent les différentes valeurs de <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> où *f*(*x*) représente la progression de l’animation et *t* représente l’heure.  
  
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
>  Vous pouvez utiliser <xref:System.Windows.Media.Animation.PowerEase> pour créer le même comportement que <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, et <xref:System.Windows.Media.Animation.QuinticEase> à l’aide de la <xref:System.Windows.Media.Animation.PowerEase.Power%2A> propriété. Par exemple, si vous souhaitez utiliser <xref:System.Windows.Media.Animation.PowerEase> pour remplacer les <xref:System.Windows.Media.Animation.CubicEase>, spécifiez un <xref:System.Windows.Media.Animation.PowerEase.Power%2A> valeur 3.  
  
 Outre l’utilisation des fonctions d’accélération incluses dans le temps d’exécution, vous pouvez créer vos propres fonctions d’accélération personnalisées en héritant de <xref:System.Windows.Media.Animation.EasingFunctionBase>. L’exemple suivant montre comment créer une fonction d’accélération personnalisée simple. Vous pouvez ajouter votre propre logique mathématique pour le comportement de la fonction d’accélération en remplaçant le <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> (méthode).   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
