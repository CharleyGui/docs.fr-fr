---
title: 'Comment : contrôler une animation avec From, To et By'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: b06df97dc57c58a01f30be2d70bfeebf104521ad
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451783"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Comment : contrôler une animation avec From, To et By
Une « from/to/by » ou une « animation de base » crée une transition entre deux valeurs cibles (consultez [vue d’ensemble](animation-overview.md) de l’animation pour une introduction aux différents types d’animations). Pour définir les valeurs cibles d’une animation de base, utilisez ses propriétés <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.  Le tableau suivant résume la façon dont les propriétés <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> peuvent être utilisées ensemble ou séparément pour déterminer les valeurs cibles d’une animation.  
  
|Propriétés spécifiées|Comportement résultant|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|L’animation passe de la valeur spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> à la valeur de base de la propriété en cours d’animation ou à la valeur de sortie d’une animation précédente, en fonction de la configuration de l’animation précédente.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|L’animation passe de la valeur spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> à la valeur spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|L’animation passe de la valeur spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> à la valeur spécifiée par la somme des propriétés <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|L’animation passe de la valeur de base de la propriété animée ou de la valeur de sortie de l’animation précédente à la valeur spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|L’animation passe de la valeur de base de la propriété animée ou de la valeur de sortie d’une animation précédente à la somme de cette valeur et de la valeur spécifiée par la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>.|  
  
> [!NOTE]
> Ne définissez pas à la fois la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> et la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> sur la même animation.  
  
 Pour utiliser d’autres méthodes d’interpolation ou effectuer une animation entre plus de deux valeurs cibles, utilisez une animation d’image clé. Pour plus d’informations, consultez [vue d’ensemble des animations d’image clé](key-frame-animations-overview.md) .  
  
 Pour plus d’informations sur l’application de plusieurs animations à une seule propriété, consultez [vue d’ensemble des animations d’image clé](key-frame-animations-overview.md).  
  
 L’exemple ci-dessous montre les différents effets de la définition des propriétés <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>et <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> sur les animations.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Exemple de valeurs cibles d’animation From, To, and By Animation Target Values Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/TargetValues)
