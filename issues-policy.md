---
ms.openlocfilehash: 33178637c4fcfb21e8190c3d2593f09326ea5995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73554847"
---
# <a name="github-issues-process-and-policy"></a>Problèmes GitHub - Processus et stratégie

Les objectifs du processus sont les suivants :

1. Vérifier que les erreurs ou omissions dans nos documents n’entravent pas la réussite des clients.
1. Réagir aux commentaires et aux préoccupations des clients.
1. Améliorer constamment l’expérience client.
1. Entamer un dialogue ouvert sur les défis et les solutions pour en savoir plus sur les expériences des clients.

Le processus comporte deux étapes pour garantir notre réactivité tout en hiérarchisant le travail. L’étape initiale diagnostique le problème et le classe. La deuxième étape résout le problème. Si un problème est à la fois simple et urgent, il est possible de combiner les deux étapes.

Le processus implique des tâches avec des allocations de temps fixes :

- Chaque membre de l’équipe consacre jusqu’à une demi-heure par jour ouvré [à la classification des problèmes entrants](#diagnosis-phase) (y compris la génération de réponses initiales). Cette approche garantit notre réactivité face aux nouveaux problèmes.
- Chaque membre de l’équipe consacre jusqu’à une demi-journée par semaine [à la mise à jour des documents](#resolution-phase) pour répondre aux problèmes GitHub générés par les clients.

## <a name="diagnosis-phase"></a>Étape de diagnostic

Chaque membre de l’équipe consacre jusqu’à 30 minutes par jour ouvré au classement des nouveaux problèmes. Nous répondons aux questions suivantes :

- Le problème est-il lié à la documentation ou au produit ?
- Serait-il préférable de poser une question dans un forum ou un site de support pour traiter ce problème ?
- Quelle est la priorité du problème ?
- Quelle zone gère ce problème ?

S’il est impossible de répondre à ces questions au cours de l’examen initial, nous demandons des clarifications dans les commentaires.

Certains types de problèmes sont fermés pendant la phase de diagnostic et de triage :

- **bravo**: Nous exprimons nos remerciements et fermons la question.
- **problème de produit**: Les questions liées au produit et non à sa documentation sont fermées. Nous pouvons également prendre des mesures supplémentaires, comme décrit ci-dessous.
- **Violations du CdC**: Ces questions sont fermées et signalées si la violation du [CdC](https://dotnetfoundation.org/code-of-conduct) mérite d’être signalée et de bloquer.
- **doublons**: Les Doublons sont fermés avec un commentaire faisant référence à la question existante.
- **doc-ok**: Le client est incorrect, et le doc est correct.
- **forum**: Les questions qui sont des demandes de soutien ou de forum sont dirigées vers Stack Overflow ou d’autres sites de support, et fermées.

### <a name="actions-on-product-issues"></a>Actions sur les problèmes de produit

Selon la nature du problème de produit, nous pouvons choisir de :

- Transférer le problème vers le dépôt de produit approprié.
- Fermer le problème s’il s’agit d’un doublon d’une demande de produit existante.
- Fermer le problème en recommandant d’ouvrir le dépôt de produit.

L’évaluation de la bonne marche à suivre est subjective. Les membres de l’équipe font appel à leur jugement pour déterminer l’action appropriée à effectuer.

### <a name="actions-on-content-issues"></a>Actions sur les problèmes de contenu

Pour les autres problèmes, l’équipe :

- Affecte une priorité.
- Affecte un jalon, généralement un « backlog ».
- Détermine si un problème peut être ajouté aux problèmes « up-for-grabs » dans les [projets des contributeurs de la communauté .NET](https://github.com/dotnet/docs/projects/35).

Les niveaux de priorité sont basés sur les recommandations suivantes, mais restent subjectifs. Les jalons, également subjectifs, sont basés sur d’autres priorités comme les planifications des versions de produit actuelles et les lancements à venir.

- **P0**: Une omission ou une erreur de docs empêche les clients de réussir dans un scénario commun.
  - Les problèmes **P0** sont traités dans un délai de trois semaines et ont priorité sur les travaux précédemment planifiés.
- **P1**: Une omission ou une erreur de docs rend un scénario courant beaucoup plus difficile ou bloque d’autres scénarios bien connus.
  - Les problèmes **P1** sont planifiés en temps utile. Souvent, les problèmes P1 sont planifiés en même temps qu’un jalon à venir.
- **P2**: Les problèmes qui causent des inconvénients mineurs, ou affectent un article de vue de basse page.
  - Les problèmes **P2** sont généralement résolus quand un article est mis à jour pour des motifs plus importants.
- **P3**: Questions qui sont des demandes de scénarios de cas de bord.
  - Les problèmes **P3** sont placés dans le backlog. Leur mise à jour est envisagée quand les articles correspondants sont mis à jour pour des motifs plus importants.

Les membres de l’équipe consacrent un temps limité au diagnostic et au triage pour faire avancer le traitement des tâches planifiées. Chaque membre de l’équipe consacre au plus 30 minutes par jour au diagnostic et au triage.

L’étiquette **up-for-grabs** est appliquée à un problème quand celui-ci est susceptible d’être corrigé par un membre de la communauté (éventuellement l’auteur). Le membre de l’équipe appliquant l’étiquette **up-for-grabs** aide les membres de la communauté à suivre le processus de création de la demande de tirage (pull request) ou trouve quelqu’un pour les aider. Les problèmes « up-for-grabs » sont souvent ajoutés aux [projets de contribution de la communauté ](https://github.com/dotnet/docs/projects/35)

> REMARQUE : Nous n’avons adopté que récemment la convention précédente. La personne qui a ajouté l’étiquette peut vous renvoyer à un autre membre de l’équipe qui vous aidera.

## <a name="resolution-phase"></a>Étape de résolution

Les problèmes générés par les clients sont pondérés dans le cadre de la planification des tâches. Chaque membre de l’équipe consacre 4 heures par semaine aux problèmes des clients ayant la priorité la plus élevée.

Le traitement d’un problème résulte du niveau de priorité défini durant le diagnostic. Les problèmes entrants des clients sont traités avec d’autres travaux planifiés de priorité similaire.

- **P0**: Dès que c’est raisonnable, au cours des trois prochaines semaines.
- **P1**: Programmé avec d’autres travaux P1 prévus. généralement dans les trois mois qui suivent.
- **P2**: Programmé avec d’autres travaux P2 prévus. Les problèmes P2 sont régulièrement planifiés en fonction de la zone et de la visibilité. Le plus souvent, les problèmes P2 sont traités lors de la mise à jour d’un article.
- **P3**: Aucune garantie sur la date fixe. Quand un article est mis à jour, nous examinons le backlog à la recherche d’autres problèmes affectant le même article.

Le niveau de priorité des problèmes peut être révisé en fonction de nouveaux commentaires et de nouvelles données sur la visibilité des articles.
