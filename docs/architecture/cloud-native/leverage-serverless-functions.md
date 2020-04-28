---
title: Exploitation des fonctions serverless
description: Tirer parti des Azure Functions sans serveur dans les applications natives du Cloud
ms.date: 04/13/2020
ms.openlocfilehash: 176499e3cd0349cd689b9d13d1c237a6343d13f3
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199740"
---
# <a name="leveraging-serverless-functions"></a>Exploitation des fonctions serverless

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Dans le spectre de la gestion des machines physiques à l’exploitation des fonctionnalités du Cloud, les vies sans serveur se trouvent à l’extrême extrémité. Votre propre responsabilité est votre code et vous payez uniquement lorsque votre code s’exécute. Azure Functions offre un moyen de créer des fonctionnalités sans serveur dans vos applications Cloud natives.

## <a name="what-is-serverless"></a>Que sont les environnements sans serveur ?

Sans serveur est un modèle de service relativement nouveau de cloud computing. Cela ne signifie pas que les serveurs sont facultatifs, votre code s’exécute toujours sur un serveur quelque part. La distinction est que l’équipe de l’application ne se soucie plus de la gestion de l’infrastructure de serveur. Au lieu de cela, il incombe au fournisseur du Cloud de s’en charger. L’équipe de développement augmente sa productivité en livrant des solutions d’entreprise aux clients, et non pas en plomb.

L’informatique sans serveur utilise des conteneurs sans état déclenchés par des événements pour héberger vos services. Ils peuvent être mis à l’échelle pour répondre à la demande en fonction des besoins. Les plateformes sans serveur telles que Azure Functions ont une intégration étroite avec d’autres services Azure tels que les files d’attente, les événements et le stockage.

## <a name="what-challenges-are-solved-by-serverless"></a>Quels sont les défis résolus sans serveur ?

Les plateformes sans serveur répondent à de nombreux problèmes fastidieux et coûteux :

- Achat de machines et de licences logicielles
- Hébergement, sécurisation, configuration et maintenance des machines et de leurs exigences en matière de mise en réseau, d’alimentation et de configuration A/C
- Mise à jour corrective et mise à niveau des systèmes d’exploitation et des logiciels
- Configuration de serveurs Web ou de services d’ordinateur pour héberger des logiciels d’application
- Configuration du logiciel d’application au sein de sa plateforme

De nombreuses entreprises allouent des budgets importants pour prendre en charge les problèmes d’infrastructure matérielle. Le passage au Cloud peut contribuer à réduire ces coûts. le déplacement d’applications vers sans serveur peut aider à les éliminer.

## <a name="what-is-the-difference-between-a-microservice-and-a-serverless-function"></a>Quelle est la différence entre un microservice et une fonction sans serveur ?

En règle générale, un microservice encapsule une fonctionnalité métier, telle qu’un panier d’achat pour un site de commerce électronique en ligne. Il expose plusieurs opérations qui permettent à un utilisateur de gérer son expérience d’achat. Toutefois, une fonction est un petit bloc de code léger qui exécute une opération à fonction unique en réponse à un événement.
Les microservices sont généralement construits pour répondre aux demandes, souvent à partir d’une interface. Les requêtes peuvent être basées sur HTTP REST ou gRPC. Les services sans serveur répondent aux événements. Son architecture pilotée par les événements est idéale pour le traitement des tâches en arrière-plan à exécution rapide.

## <a name="what-scenarios-are-appropriate-for-serverless"></a>Quels sont les scénarios appropriés pour les serveurs sans serveur ?

Sans serveur expose des fonctions individuelles à exécution réduite qui sont appelées en réponse à un déclencheur. Cela les rend idéaux pour le traitement des tâches en arrière-plan.

Une application peut être amenée à envoyer un message électronique en tant qu’étape dans un flux de travail. Au lieu d’envoyer la notification dans le cadre d’une demande de microservice, placez les détails du message dans une file d’attente. Une fonction Azure peut mettre le message en file d’attente et l’envoyer de façon asynchrone. Cela pourrait améliorer les performances et l’extensibilité du microservice. Le nivellement de la [charge basé sur une file d’attente](https://docs.microsoft.com/azure/architecture/patterns/queue-based-load-leveling) peut être mis en œuvre pour éviter les goulots d’étranglement liés à l’envoi des e-mails. En outre, ce service autonome peut être réutilisé en tant qu’utilitaire dans de nombreuses applications différentes.

La messagerie asynchrone à partir des files d’attente et des rubriques est un modèle courant pour déclencher des fonctions sans serveur. Toutefois, les Azure Functions peuvent être déclenchés par d’autres événements, tels que les modifications apportées au stockage d’objets BLOB Azure. Un service qui prend en charge les chargements d’image peut avoir une fonction Azure chargée de l’optimisation de la taille de l’image. La fonction peut être déclenchée directement par les insertions dans le stockage d’objets BLOB Azure, ce qui complique les opérations de microservice.

De nombreux services ont des processus de longue durée dans le cadre de leurs flux de travail. Ces tâches sont souvent effectuées dans le cadre de l’interaction de l’utilisateur avec l’application. Ces tâches peuvent forcer l’utilisateur à attendre, ce qui a un impact négatif sur son expérience. L’informatique sans serveur offre un excellent moyen de déplacer des tâches plus lentes en dehors de la boucle d’interaction avec l’utilisateur. Ces tâches peuvent être mises à l’échelle avec la demande sans nécessiter une mise à l’échelle complète de l’application.

## <a name="when-should-you-avoid-serverless"></a>Quand faut-il éviter les sans serveur ?

Des solutions sans serveur approvisionnent et évoluent à la demande. Quand une nouvelle instance est appelée, le démarrage à froid est un problème courant. Un démarrage à froid correspond à la durée nécessaire à la configuration de cette instance. En règle générale, ce délai peut être de quelques secondes, mais peut être plus long en fonction de différents facteurs. Une fois approvisionnée, une seule instance reste active tant qu’elle reçoit des demandes périodiques. Toutefois, si un service est appelé moins fréquemment, Azure peut le supprimer de la mémoire et nécessiter un démarrage à froid lorsqu’il est rappelé. Les démarrages à froid sont également requis quand une fonction s’ajuste à une nouvelle instance.

La figure 3-10 montre un modèle de démarrage à froid. Notez les étapes supplémentaires requises lorsque l’application est froide.

![Le démarrage](./media/cold-start-warm-start.png)
à froid et à chaud**figure 3-10**. Démarrage à froid et démarrage à chaud.

Pour éviter tout démarrage à froid, vous pouvez passer d’un [plan de consommation à un plan dédié](https://azure.microsoft.com/blog/understanding-serverless-cold-start/). Vous pouvez également configurer une ou plusieurs [instances préchauffées](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances) avec la mise à niveau du plan Premium. Dans ce cas, lorsque vous devez ajouter une autre instance, celle-ci est déjà opérationnelle et prête à l’emploi. Ces options peuvent aider à atténuer le problème de démarrage à froid associé à l’informatique sans serveur.

Les fournisseurs de Cloud facturent des factures sans serveur en fonction du temps d’exécution du calcul et de la mémoire consommée. Les opérations de longue durée ou de consommation de mémoire élevée ne sont pas toujours les meilleurs candidats pour l’exécution sans serveur. Les fonctions sans serveur favorisent de petits segments de travail qui peuvent se terminer rapidement. La plupart des plates-formes sans serveur requièrent l’exécution de fonctions individuelles en quelques minutes. Azure Functions est défini par défaut sur une durée de délai d’attente de 5 minutes, qui peut être configurée jusqu’à 10 minutes. Le plan Azure Functions Premium peut également atténuer ce problème, et les délais d’expiration par défaut sont de 30 minutes avec une limite supérieure illimitée pouvant être configurée. L’heure de calcul n’est pas une heure de calendrier. Les fonctions plus avancées utilisant [Azure durable Functions Framework](https://docs.microsoft.com/azure/azure-functions/durable/durable-functions-overview?tabs=csharp) peuvent suspendre l’exécution pendant plusieurs jours. La facturation est basée sur la durée d’exécution réelle-lorsque la fonction sort de veille et reprend le traitement.

Enfin, tirer parti de Azure Functions pour les tâches d’application complique la tâche. Il est judicieux de commencer par concevoir votre application avec une conception modulaire et faiblement couplée. Ensuite, déterminez s’il existe des avantages sans serveur qui justifient la complexité supplémentaire.

>[!div class="step-by-step"]
>[Précédent](leverage-containers-orchestrators.md)
>[suivant](combine-containers-serverless-approaches.md)
