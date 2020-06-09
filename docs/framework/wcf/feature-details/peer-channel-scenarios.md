---
title: Scénarios de canal homologue
ms.date: 03/30/2017
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
ms.openlocfilehash: c4c24a0bafa4f73760d02de6242a9ed438d7d60e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596875"
---
# <a name="peer-channel-scenarios"></a>Scénarios de canal homologue
Les API de canal homologue prennent en charge les scénarios de développement suivants.  
  
## <a name="publicationsubscription-messaging"></a>Messagerie de publication/abonnement  
 Les sociétés qui créent des applications de publication/abonnement (par exemple, téléscripteurs pour le marché boursier ou éditeurs de titres de l'actualité, de résultats sportifs et de bulletins météorologiques) peuvent appliquer le canal homologue à des applications sans serveur. Par exemple, les utilisateurs peuvent obtenir les derniers résultats sportifs en rejoignant une maille commune (ou groupe de clients) et propager le volume important des données mises à jour concernant les rencontres sans augmenter la charge des serveurs. Ce système permet au fournisseur de données d'améliorer la qualité du service sans augmenter de manière importante l'investissement dans les technologies serveur.  
  
## <a name="collaboration"></a>Collaboration  
 Les éditeurs de logiciels indépendants peuvent créer des applications qui permettent aux personnes de former des groupes restreints pour participer à des activités d'égal à égal. Il peut s’agir notamment de travaux d’équipe dans le cadre de projets concertés, de partage d’images entre amis, de tâches liées à la préparation d’une fête, etc. D'ordinaire, ces activités impliquent toujours des serveurs. Toutefois, le canal homologue offre une manière de procéder plus rentable en prenant en charge des scénarios d'accès hors connexion plus difficiles à implémenter dans un modèle de client-serveur classique.  
  
## <a name="distributed-processing-and-compute-clusters"></a>Traitement distribué et clusters de calcul  
 Les clusters de calcul et le traitement distribué s'utilisent normalement pour effectuer des calculs à grande échelle, tels que la modélisation financière/météorologique et le décodage du génome humain. En général, il s’agit pour les serveurs d’affecter des tâches à tous les clients participant au cluster de calcul. Ces serveurs peuvent également imposer des exigences supplémentaires ; par exemple, exécuter toutes les tâches dans un délai défini, ce qui nécessite de mobiliser plusieurs ordinateurs sur chaque tâche. Par ailleurs, si un client qui exécute une tâche rencontre une défaillance, un autre client doit être en mesure de prendre le relais et d’effectuer la tâche. De même, plusieurs clients peuvent devoir exécuter la même tâche pour garantir des résultats cohérents. Bien que les serveurs puissent exécuter ce type de coordination de clients, vous pouvez créer une solution d’égal à égal dans laquelle les clients chargés d’une tâche déterminent de manière indépendante les exigences du serveur relatives à la tâche et utilisent une maille de calcul pour savoir comment accomplir cette tâche.  
  
## <a name="gaming"></a>Jeux  
 À l’aide du canal homologue, les développeurs d’applications peuvent créer des versions sans serveur de leurs jeux dans lesquels les mouvements sont transmis et synchronisés à d’autres joueurs par un mécanisme d’égal à égal plutôt que par l’intermédiaire d’un serveur central. Pour les petits éditeurs de logiciels indépendants, cette technique supprime les coûts d'exploitation associés au déploiement, à la gestion et à l'entretien de serveurs centraux. Les jeux écrits à l'aide d'une architecture d'égal à égal peuvent être utilisés sur Internet, ou sur des réseaux locaux câblés ou sans fil. Les activités secondaires des jeux, telles que les salles de rencontre et les conversations en cours de jeu, peuvent être développées à l'aide d'un réseau P2P.  
  
## <a name="see-also"></a>Voir aussi

- [Concepts relatifs au canal homologue](peer-channel-concepts.md)
