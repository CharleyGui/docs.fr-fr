---
title: 'Procédure : Contrôler une animation avec From, To et By'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: 812217a2905671567271687b974a435dd85cea47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930089"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>Procédure : Contrôler une animation avec From, To et By
Une «from/to/by» ou une «animation de base» crée une transition entre deux valeurs cibles (consultez [vue d’ensemble](animation-overview.md) de l’animation pour une introduction aux différents types d’animations). Pour définir les valeurs cibles d’une animation de base, utilisez <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>ses <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>propriétés, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> et.  Le tableau suivant résume la façon dont <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>les <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>propriétés, <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> et peuvent être utilisées ensemble ou séparément pour déterminer les valeurs cibles d’une animation.  
  
|Propriétés spécifiées|Comportement résultant|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|L’animation passe de la valeur spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété à la valeur de base de la propriété en cours d’animation ou à la valeur de sortie d’une animation précédente, en fonction de la configuration de l’animation précédente.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|L’animation passe de la valeur spécifiée par <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> la propriété à la valeur spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> propriété.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|L’animation passe de la valeur spécifiée par la <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> propriété à la valeur spécifiée par la somme <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> des propriétés et <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> .|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|L’animation passe de la valeur de base de la propriété animée ou de la valeur de sortie d’une animation précédente à la <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> valeur spécifiée par la propriété.|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|L’animation passe de la valeur de base de la propriété animée ou de la valeur de sortie d’une animation précédente à la somme de cette valeur et de la valeur <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> spécifiée par la propriété.|  
  
> [!NOTE]
> Ne définissez pas à la <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> fois la propriété <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A> et la propriété sur la même animation.  
  
 Pour utiliser d’autres méthodes d’interpolation ou effectuer une animation entre plus de deux valeurs cibles, utilisez une animation d’image clé. Pour plus d’informations, consultez [vue d’ensemble des animations d’image clé](key-frame-animations-overview.md) .  
  
 Pour plus d’informations sur l’application de plusieurs animations à une seule propriété, consultez [vue d’ensemble des animations d’image clé](key-frame-animations-overview.md).  
  
 L’exemple ci-dessous montre les différents effets <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>de <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>la définition <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> des propriétés, et sur les animations.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Exemple de valeurs cibles d’animation From, To et By](https://go.microsoft.com/fwlink/?LinkID=159988)
