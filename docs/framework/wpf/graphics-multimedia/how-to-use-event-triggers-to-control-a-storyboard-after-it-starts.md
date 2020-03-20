---
title: "Comment : utiliser des déclencheurs d'événements pour contrôler un storyboard après son démarrage"
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 518f5d7ea0b5dc00677489f1383814563c565145
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186704"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Comment : utiliser des déclencheurs d'événements pour contrôler un storyboard après son démarrage

Cet exemple montre comment <xref:System.Windows.Media.Animation.Storyboard> contrôler un après qu’il commence. Pour commencer <xref:System.Windows.Media.Animation.Storyboard> par [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]utiliser <xref:System.Windows.Media.Animation.BeginStoryboard>, utiliser , qui distribue les animations aux objets et aux propriétés qu’ils animent, puis commence le storyboard. Si vous <xref:System.Windows.Media.Animation.BeginStoryboard> donnez un nom <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> en spécifiant sa propriété, vous en faites un storyboard contrôlable. Vous pouvez ensuite contrôler interactivement le storyboard après qu’il commence.

Utilisez les actions suivantes <xref:System.Windows.EventTrigger> de storyboard avec des objets pour contrôler un storyboard.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Pauses du storyboard.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Reprend un storyboard en pause.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Change la vitesse du storyboard.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Avance un storyboard jusqu’à la fin de sa période de remplissage, s’il en a un.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Arrête le storyboard.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Supprime le storyboard, libérant des ressources.

## <a name="example"></a> Exemple

L’exemple suivant utilise des actions de storyboard contrôlables pour contrôler de manière interactive un storyboard.

> [!NOTE]
> Pour voir un exemple de contrôle d’un storyboard en utilisant du code, voir [Contrôlez un storyboard après qu’il commence à utiliser ses méthodes interactives](how-to-control-a-storyboard-after-it-starts.md).

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

Pour d’autres exemples, voir [l’Animation Exemple Galerie](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [Contrôler une table de montage séquentiel après son démarrage à l’aide de ses méthodes interactives](how-to-control-a-storyboard-after-it-starts.md)
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des plans conceptuels](storyboards-overview.md)
