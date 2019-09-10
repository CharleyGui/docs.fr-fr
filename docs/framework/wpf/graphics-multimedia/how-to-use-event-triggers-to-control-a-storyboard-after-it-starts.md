---
title: 'Procédure : Utiliser des déclencheurs d’événements pour contrôler une table de montage séquentiel après son démarrage'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 32591edd065a8122b84ff14102f672ccf6001d67
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855846"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Procédure : Utiliser des déclencheurs d’événements pour contrôler une table de montage séquentiel après son démarrage

Cet exemple montre comment contrôler un <xref:System.Windows.Media.Animation.Storyboard> après son démarrage. Pour démarrer un <xref:System.Windows.Media.Animation.Storyboard> à l' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]aide de <xref:System.Windows.Media.Animation.BeginStoryboard>, utilisez, qui distribue les animations aux objets et propriétés qu’ils animent, puis démarre le Storyboard. Si vous donnez <xref:System.Windows.Media.Animation.BeginStoryboard> un nom en spécifiant <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> sa propriété, vous en faites une table de montage séquentiel contrôlable. Vous pouvez ensuite contrôler de manière interactive le storyboard après son démarrage.

Utilisez les actions de Storyboard suivantes avec <xref:System.Windows.EventTrigger> des objets pour contrôler une table de montage séquentiel.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Suspend le Storyboard.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Reprend une table de montage séquentiel suspendue.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Modifie la vitesse de la table de montage séquentiel.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Fait avancer un Storyboard jusqu’à la fin de sa période de remplissage, le cas échéant.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Arrête le Storyboard.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Supprime le Storyboard, en libérant des ressources.

## <a name="example"></a>Exemple

L’exemple suivant utilise des actions de Storyboard contrôlable pour contrôler de manière interactive une table de montage séquentiel.

> [!NOTE]
> Pour voir un exemple de contrôle d’une table de montage séquentiel à l’aide de code, consultez [contrôler une table de montage séquentiel après son démarrage à l’aide de ses méthodes interactives](how-to-control-a-storyboard-after-it-starts.md).

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

Pour obtenir des exemples supplémentaires, consultez la Galerie d’exemples d' [animation](https://go.microsoft.com/fwlink/?LinkID=159969).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [Contrôler un storyboard après son démarrage à l'aide de ses méthodes interactives](how-to-control-a-storyboard-after-it-starts.md)
- [Vue d’ensemble de l’animation](animation-overview.md)
- [Vue d'ensemble des plans conceptuels](storyboards-overview.md)
