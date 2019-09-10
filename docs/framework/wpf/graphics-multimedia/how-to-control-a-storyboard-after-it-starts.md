---
title: 'Procédure : Contrôler un storyboard après son démarrage'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: de30cfdb49df721cb4d6845dc67464e8a5b61f93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855865"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>Procédure : Contrôler un storyboard après son démarrage

Cet exemple montre comment utiliser du code pour contrôler un <xref:System.Windows.Media.Animation.Storyboard> après son démarrage. Pour contrôler un Storyboard dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], utilisez <xref:System.Windows.Trigger> les <xref:System.Windows.TriggerAction> objets et ; pour obtenir un exemple, consultez [utiliser des déclencheurs d’événements pour contrôler un storyboard après son démarrage](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

Pour démarrer une table de montage séquentiel, <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> vous utilisez sa méthode, qui distribue les animations de la table de montage séquentiel aux propriétés qu’elles animent et démarre le Storyboard.

Pour rendre un Storyboard contrôlable, vous utilisez la <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> méthode et spécifiez **true** comme deuxième paramètre. Vous pouvez ensuite utiliser les méthodes interactives de la table de montage séquentiel pour suspendre, reprendre, Rechercher, arrêter, accélérer ou ralentir le Storyboard, ou l’avancer jusqu’à sa période de remplissage. Voici une liste des méthodes interactives de la table de montage séquentiel :

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Suspend le Storyboard.

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Reprend une table de montage séquentiel suspendue.

- <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Définit la vitesse interactive de la table de montage séquentiel.

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Recherche l’emplacement spécifié dans le Storyboard.

- <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Recherche le Storyboard à l’emplacement spécifié. Contrairement à <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> la méthode, cette opération est traitée avant le cycle suivant.

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Fait avancer le Storyboard jusqu’à sa période de remplissage, le cas échéant.

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Arrête le Storyboard.

Dans l’exemple suivant, plusieurs méthodes de Storyboard sont utilisées pour contrôler de manière interactive une table de montage séquentiel.

> [!NOTE]
> Pour voir un exemple de contrôle d’une table de montage séquentiel [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]à l’aide de déclencheurs avec, consultez [utiliser des déclencheurs d’événements pour contrôler un storyboard après son démarrage](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

## <a name="example"></a>Exemple

[!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
[!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]

## <a name="see-also"></a>Voir aussi

- [Utiliser des déclencheurs d’événements pour contrôler un storyboard après son démarrage](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
