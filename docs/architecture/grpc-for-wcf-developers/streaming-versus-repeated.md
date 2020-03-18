---
title: Services de streaming vs champs répétés - gRPC pour les développeurs WCF
description: Comparez les champs répétés aux services de streaming comme moyens de transmettre des collections de données en utilisant gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 542ebc393f9c9c1ad717d02d01fab33d85c18917
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147748"
---
# <a name="grpc-streaming-services-vs-repeated-fields"></a>Services de streaming gRPC et champs répétés

les services gRPC fournissent deux façons de retourner des jeux de données, ou des listes d’objets. La spécification du message Protocol `repeated` Buffers utilise le mot clé pour déclarer des listes ou des pansements de messages dans un autre message. La spécification de service gRPC utilise le `stream` mot clé pour déclarer une connexion persistante de longue durée. Au-dessus de cette connexion, plusieurs messages sont envoyés et peuvent être traités individuellement.

Vous pouvez également `stream` utiliser la fonctionnalité pour des données temporelles de longue durée telles que des notifications ou des messages journalaux. Mais ce chapitre examinera son utilisation pour le retour d’un ensemble de données unique.

Ce que vous devez utiliser dépend de facteurs tels que :

- La taille globale de l’ensemble de données.
- Le temps qu’il a fallu pour créer le jeu de données à l’extrémité du client ou du serveur.
- Si le consommateur de l’ensemble de données peut commencer à agir sur elle dès que le premier élément est disponible, ou a besoin de l’ensemble de données complet pour faire quelque chose d’utile.

## <a name="when-to-use-repeated-fields"></a>Quand utiliser `repeated` les champs

Pour tout jeu de données qui est limité dans la taille et qui peut être généré dans son `repeated` intégralité dans un court laps de temps- disons, moins d’une seconde, vous devriez utiliser un champ dans un message Protobuf régulier. Par exemple, dans un système de commerce électronique, construire une liste d’éléments dans une commande est probablement rapide et la liste ne sera pas très grande. Le retour d’un seul message avec `repeated` un `stream` champ est un ordre de grandeur plus rapide que l’utilisation et engage moins de frais généraux réseau.

Si le client a besoin de toutes les données avant de commencer à les `repeated` traiter et que le jeu de données est assez petit pour être construit en mémoire, alors envisagez d’utiliser un champ. Considérez-le même si la création de l’ensemble de données dans la mémoire sur le serveur est plus lente.

## <a name="when-to-use-stream-methods"></a>Quand utiliser `stream` des méthodes

Lorsque les objets de message dans vos jeux de données sont potentiellement très volumineux, il est préférable pour vous de les transférer en utilisant des demandes ou des réponses en streaming. Il est plus efficace de construire un grand objet dans la mémoire, l’écrire au réseau, puis libérer les ressources. Cette approche améliorera l’évolutivité de votre service.

De même, vous devez envoyer des jeux de données de taille sans contrainte sur les flux pour éviter de manquer de mémoire tout en les construisant.

Pour les ensembles de données où le consommateur peut traiter séparément chaque élément, vous devriez envisager d’utiliser un flux si cela signifie que les progrès peuvent être indiqués à l’utilisateur. L’utilisation d’un flux peut améliorer la réactivité d’une application, mais vous devez l’équilibrer par rapport aux performances globales de l’application.

Un autre scénario où les flux peuvent être utiles est l’endroit où un message est traité sur plusieurs services. Si chaque service d’une chaîne renvoie un flux, le service terminal (c’est-à-dire le dernier de la chaîne) peut commencer à retourner des messages. Ces messages peuvent être traités et transmis le long de la chaîne au demandeur d’origine. Le demandeur peut soit retourner un flux, soit agréger les résultats en un seul message de réponse. Cette approche se prête bien à des modèles comme MapReduce.

>[!div class="step-by-step"]
>[Suivant précédent](migrate-duplex-services.md)
>[Next](client-libraries.md)
