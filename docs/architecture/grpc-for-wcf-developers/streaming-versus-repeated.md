---
title: Services de streaming et champs répétés-gRPC pour les développeurs WCF
description: Comparez les champs répétés aux services de streaming pour passer des collections de données à l’aide de gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 0e717df57ba2bb52d63a063072d8a45bf0f7e395
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503374"
---
# <a name="grpc-streaming-services-vs-repeated-fields"></a>services de streaming gRPC et champs répétés

les services gRPC offrent deux moyens de retourner des jeux de données ou des listes d’objets. La spécification de message de mémoires tampons de protocole utilise le mot clé `repeated` pour déclarer des listes ou des tableaux de messages dans un autre message. La spécification du service gRPC utilise le mot clé `stream` pour déclarer une connexion permanente longue. Sur cette connexion, plusieurs messages sont envoyés et peuvent être traités individuellement. 

Vous pouvez également utiliser la fonctionnalité `stream` pour les données temporelles de longue durée, telles que les notifications ou les messages de journal. Mais ce chapitre prend en compte son utilisation pour retourner un jeu de données unique.

Ce que vous devez utiliser dépend de facteurs tels que :

- Taille globale du jeu de données.
- Le temps nécessaire pour créer le jeu de données à la fin du client ou du serveur.
- Si le consommateur du DataSet peut commencer à agir dessus dès que le premier élément est disponible, ou si le jeu de données complet doit faire l’objet d’une action utile.

## <a name="when-to-use-repeated-fields"></a>Quand utiliser les champs de `repeated`

Pour tout jeu de données limité en taille et pouvant être généré dans son intégralité dans un laps de temps donné (par exemple, sous une seconde), vous devez utiliser un champ `repeated` dans un message Protobuf normal. Par exemple, dans un système de commerce électronique, la création d’une liste d’éléments dans une commande est probablement rapide et la liste n’est pas très volumineuse. Le retour d’un seul message avec un champ `repeated` est un ordre de grandeur plus rapide que l’utilisation de `stream` et entraîne moins de surcharge du réseau.

Si le client a besoin de toutes les données avant de commencer à le traiter et que le jeu de données est suffisamment petit pour être construit en mémoire, envisagez d’utiliser un champ `repeated`. Considérez-le même si la création du jeu de données en mémoire sur le serveur est plus lente.

## <a name="when-to-use-stream-methods"></a>Quand utiliser des méthodes `stream`

Lorsque les objets de message de vos jeux de données sont potentiellement très volumineux, il est préférable de les transférer à l’aide de demandes de diffusion en continu ou de réponses. Il est plus efficace de construire un objet volumineux en mémoire, de l’écrire sur le réseau, puis de libérer les ressources. Cette approche permet d’améliorer l’évolutivité de votre service.

De même, vous devez envoyer des jeux de données de taille non contrainte sur des flux pour éviter de manquer de mémoire lors de leur construction.

Pour les jeux de données où le consommateur peut traiter séparément chaque élément, vous devez envisager d’utiliser un flux si cela signifie que la progression peut être indiquée à l’utilisateur. L’utilisation d’un flux peut améliorer la réactivité d’une application, mais vous devez l’équilibrer par rapport aux performances globales de l’application.

Un autre scénario dans lequel les flux peuvent être utiles est l’endroit où un message est traité sur plusieurs services. Si chaque service d’une chaîne retourne un flux, le service Terminal (autrement dit, le dernier de la chaîne) peut commencer à retourner des messages. Ces messages peuvent être traités et renvoyés le long de la chaîne au demandeur d’origine. Le demandeur peut retourner un flux ou agréger les résultats dans un message de réponse unique. Cette approche se prête bien à des modèles tels que MapReduce.

>[!div class="step-by-step"]
>[Précédent](migrate-duplex-services.md)
>[Suivant](client-libraries.md)
