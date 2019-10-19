---
title: Exploitation des fonctions serverless
description: Tirer parti des Azure Functions sans serveur dans les applications natives du Cloud
ms.date: 06/30/2019
ms.openlocfilehash: c79f611b83f63079634fb2bac037c99f851f18ab
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578922"
---
# <a name="leveraging-serverless-functions"></a>Exploitation des fonctions serverless

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Dans le spectre de la gestion des ordinateurs complets et des systèmes d’exploitation pour tirer parti des fonctionnalités du Cloud, la vie sans serveur se fait à l’extrême extrémité où la seule chose dont vous êtes responsable est votre code, et vous payez uniquement quand votre code s’exécute. Azure Functions offre un moyen de créer des fonctionnalités sans serveur dans vos applications. 

## <a name="what-is-serverless"></a>Qu’est-ce que sans serveur ?

L’informatique sans serveur ne signifie pas qu’aucun serveur n’est impliqué dans l’exécution de votre application. le code s’exécute toujours sur un serveur quelque part. La distinction est que l’équipe de développement d’applications n’a plus à se préoccuper de la gestion de l’infrastructure de serveur. Les solutions informatiques sans serveur comme Azure Functions aident les équipes à augmenter leur productivité et à permettre aux organisations d’optimiser leurs ressources et de se concentrer sur la diffusion de solutions.

L’informatique sans serveur utilise des conteneurs sans état déclenchés par des événements pour héberger votre application ou une partie de votre application. Les plateformes sans serveur peuvent monter en puissance et dans pour répondre à la demande en fonction des besoins. Les plateformes telles que Azure Functions ont un accès direct facile à d’autres services Azure tels que les files d’attente, les événements et le stockage.

## <a name="what-challenges-are-solved-by-serverless"></a>Quels sont les défis résolus sans serveur ?

Sans serveur est l’abstraction ultime de l’exécution de votre propre matériel. Les développeurs peuvent se concentrer exclusivement sur l’écriture de code pour résoudre les problèmes d’entreprise, sans se préoccuper des tâches suivantes qui peuvent être nécessaires lors de l’hébergement de vos propres serveurs :

- Achat de machines et de licences logicielles
- Hébergement, sécurisation, configuration et maintenance des machines et de leurs exigences en matière de mise en réseau, d’alimentation et de configuration A/C
- Mise à jour corrective et mise à niveau des systèmes d’exploitation et des logiciels
- Configuration de serveurs Web ou de services d’ordinateur pour héberger des logiciels d’application
- Configuration du logiciel d’application au sein de sa plateforme

De nombreuses entreprises utilisent des dizaines de membres du personnel et allouent de grands budgets pour prendre en charge ces problèmes d’infrastructure matérielle. Le simple déplacement vers le Cloud élimine certains de ces problèmes. le décalage des applications jusqu’au mode sans serveur élimine le reste.

## <a name="what-scenarios-are-appropriate-for-serverless"></a>Quels sont les scénarios appropriés pour les serveurs sans serveur ?

Sans serveur utilise des fonctions individuelles à exécution réduite qui sont appelées en réponse à un déclencheur. Cela les rend idéaux pour le traitement des tâches en arrière-plan.

Par exemple, une application peut être amenée à envoyer un message électronique dans le cadre du traitement d’une demande. Au lieu d’envoyer l’e-mail dans le cadre de la gestion de la demande Web, les détails de l’e-mail peuvent être placés dans une file d’attente et une fonction Azure peut être utilisée pour récupérer le message et envoyer l’e-mail. De nombreuses parties différentes de l’application, voire de nombreuses applications, peuvent tirer parti de cette même fonction Azure, ce qui permet d’améliorer les performances et l’évolutivité des applications et d’utiliser le [nivellement de charge basé sur les files d’attente](https://docs.microsoft.com/azure/architecture/patterns/queue-based-load-leveling) pour éviter les goulots d’étranglement liés à envoi des e-mails.

Bien qu’un modèle de serveur de [publication/d’abonné](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) entre les applications et les Azure Functions est le modèle le plus courant, d’autres modèles sont possibles. Les Azure Functions peuvent être déclenchés par d’autres événements, tels que les modifications apportées au stockage d’objets BLOB Azure. Une application qui prenait en charge les chargements d’image peut avoir une fonction Azure chargée de créer des images miniatures, ou de redimensionner des images téléchargées vers des dimensions cohérentes, ou d’optimiser la taille de l’image. Toutes ces fonctionnalités peuvent être déclenchées directement par les insertions dans le stockage d’objets BLOB Azure, ce qui réduit la complexité et la charge de travail de l’application elle-même.

De nombreuses applications ont des processus de longue durée dans le cadre de leurs flux de travail. Ces tâches sont souvent effectuées dans le cadre de l’interaction de l’utilisateur avec l’application, ce qui oblige l’utilisateur à attendre et à avoir un impact négatif sur son expérience. L’informatique sans serveur offre un excellent moyen d’effectuer des tâches plus lentes en dehors de la boucle d’interaction utilisateur, et ces tâches peuvent facilement évoluer avec la demande sans nécessiter une mise à l’échelle complète de l’application.

## <a name="when-should-you-avoid-serverless"></a>Quand faut-il éviter les sans serveur ?

L’informatique sans serveur est mieux utilisée pour les tâches qui ne bloquent pas l’interface utilisateur. Cela signifie qu’elles ne sont pas idéales pour héberger des applications Web ou des API Web directement. La raison principale est que les solutions sans serveur sont approvisionnées et mises à l’échelle à la demande. Lorsqu’une nouvelle instance d’une fonction est nécessaire, désignée sous le terme de *démarrage à froid*, son approvisionnement prend du temps. Cette durée est généralement de quelques secondes, mais elle peut être plus longue en fonction d’un grand nombre de facteurs. Une instance unique peut souvent rester active indéfiniment (par exemple, en effectuant régulièrement une demande), mais le problème de démarrage à froid subsiste si le nombre d’instances doit être mis à l’échelle.

![Cold par rapport au démarrage à chaud ](./media/cold-start-warm-start.png)
 la**Figure 3-10**. Démarrage à froid et démarrage à chaud.

Si vous devez éviter que le démarrage à froid ne démarre entièrement, vous pouvez choisir de passer d’un [plan de consommation à un plan dédié](https://azure.microsoft.com/blog/understanding-serverless-cold-start/). Vous pouvez également [configurer une ou plusieurs instances prédéfinies](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances) avec le plan Premium. ainsi, lorsque vous devez ajouter une autre instance, celle-ci est déjà opérationnelle et prête à l’emploi. Ces options peuvent atténuer l’un des problèmes clés associés à l’informatique sans serveur.

En général, vous devez également éviter les tâches sans serveur pour les tâches de longue durée. Elles sont idéales pour les petits éléments de travail qui peuvent être effectués rapidement. La plupart des plates-formes sans serveur requièrent l’exécution de fonctions individuelles en quelques minutes. Azure Functions a pour valeur par défaut une durée de délai d’attente de 5 minutes (peut être configurée jusqu’à 10 minutes). Le plan Azure Functions Premium peut également atténuer ce problème, le délai d’expiration par défaut étant de 30 minutes et la configuration d’une limite supérieure illimitée.

Enfin, l’utilisation de sans serveur pour certaines tâches au sein de votre application complique la tâche. Il est souvent préférable d’abord concevoir votre application de manière modulaire et faiblement couplée, puis d’identifier s’il existe des avantages sans serveur, ce qui rend la complexité supplémentaire utile. De nombreuses applications plus petites s’exécutent parfaitement bien dans un déploiement monolithique unique, sans qu’il soit nécessaire de recourir à l’architecture d’application distribuée.

## <a name="references"></a>Références

- [Fonctionnement du démarrage à froid sans serveur](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [Instances de Azure Functions préchauffées](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [Créer une fonction sur Linux à l’aide d’une image personnalisée](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)

>[!div class="step-by-step"]
>[Précédent](leverage-containers-orchestrators.md)
>[Suivant](combine-containers-serverless-approaches.md)
