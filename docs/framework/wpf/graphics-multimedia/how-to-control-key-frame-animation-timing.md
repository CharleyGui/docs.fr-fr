---
title: "Comment : contrôler le minutage d'une animation d'image clé"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-frame animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 8cfd2be0bbc526ed92a5fb1b558a5a41dc9c3113
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344732"
---
# <a name="how-to-control-key-frame-animation-timing"></a>Comment : contrôler le minutage d'une animation d'image clé

Cet exemple montre comment contrôler le timing des cadres clés dans une animation à cadre clé. Comme d’autres animations, les <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animations à cadre clé ont une propriété. En plus de spécifier la durée d’une animation, vous devez spécifier quelle partie de cette durée est allouée à chacun de ses cadres clés. Pour allouer le temps, vous spécifiez un <xref:System.Windows.Media.Animation.KeyTime> pour chaque cadre clé de l’animation.

Le <xref:System.Windows.Media.Animation.KeyTime> pour chaque cadre de clé spécifie quand un cadre de clé se termine (il ne spécifie pas la durée d’un cadre clé joue). Vous pouvez <xref:System.Windows.Media.Animation.KeyTime> spécifier une <xref:System.TimeSpan> valeur, en <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> pourcentage ou comme valeur spéciale.

## <a name="example"></a>Exemple

L’exemple suivant <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> utilise un rectangle pour animer l’écran. Les temps clés des cadres <xref:System.TimeSpan> sont définis avec des valeurs.

[!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
[!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
[!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]

L’illustration suivante montre quand la valeur de chaque cadre clé est atteinte.

![Valeurs de clés atteintes à 3, 4 et 10 secondes](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")

L’exemple suivant montre une animation identique, sauf que les temps clés des cadres sont définis avec des valeurs en pourcentage.

[!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
[!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
[!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]

L’illustration suivante montre quand la valeur de chaque cadre clé est atteinte.

![Valeurs de clés atteintes à 3, 4 et 10 secondes](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")

L’exemple <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> suivant utilise des valeurs temporelles clés.

[!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
[!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
[!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]

L’illustration suivante montre quand la valeur de chaque cadre clé est atteinte.

![Valeurs de clés atteintes à 3,3, 6,6 et 9,9 secondes](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")

L’exemple <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> final utilise des valeurs temporelles clés.

[!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
[!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
[!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]

L’illustration suivante montre quand la valeur de chaque cadre clé est atteinte.

![Valeurs de clés atteintes à 0, 5 et 10 secondes](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")

Par souci de simplicité, les versions de code de cet exemple utilisent des animations locales, et non des storyboards, car seule une seule animation est appliquée à une seule propriété, mais les exemples peuvent être modifiés pour utiliser des storyboards à la place. Pour un exemple montrant comment déclarer un storyboard dans le code, voir [Animate une propriété en utilisant un storyboard](how-to-animate-a-property-by-using-a-storyboard.md).

Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation). Pour plus d’informations sur les animations de cadres clés, consultez le [Aperçu des animations Key-Frame](key-frame-animations-overview.md).

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble des animations d'image clé](key-frame-animations-overview.md)
- [Vue d'ensemble de l'animation](animation-overview.md)
- [Rubriques Comment](animation-and-timing-how-to-topics.md)
