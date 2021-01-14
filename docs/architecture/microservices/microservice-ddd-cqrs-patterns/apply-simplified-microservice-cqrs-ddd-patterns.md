---
title: Application de modèles CQRS et DDD simplifiés dans un microservice
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre la relation globale entre les modèles CQRS et DDD.
ms.date: 01/13/2021
ms.openlocfilehash: c1a990689a446e2efba48beafe4b55d614b54427
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188957"
---
# <a name="apply-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Appliquer des modèles CQRS et DDD simplifiés dans un microservice

CQRS est un modèle d’architecture qui sépare les modèles pour la lecture et l’écriture de données. Le terme lié à la [séparation des requêtes de commande (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) a été initialement défini par Bertrand Meyer dans sa *construction logicielle orientée objet*. L’idée de base est que vous pouvez diviser les opérations d’un système en deux catégories fortement séparées :

- Requêtes. Ces requêtes retournent un résultat et ne modifient pas l’état du système, et elles ne sont pas des effets secondaires.

- Les commandes. Ces commandes modifient l’état d’un système.

CQS est un concept simple : il s’agit des méthodes dans le même objet qui sont des requêtes ou des commandes. Chaque méthode retourne l’état ou transforme l’état, mais pas les deux. Même un seul objet de modèle de dépôt peut se conformer à CQS. L’approche CQS peut être considérée comme un principe fondamental de CQRS.

L’approche [CQRS (séparation des responsabilités dans les commandes et les requêtes)](https://martinfowler.com/bliki/CQRS.html), introduite par Greg Young, a été vivement plébiscitée par Udi Dahan et d’autres. Elle est basée sur le principe CQS, même si elle est plus détaillée. Elle peut être considérée comme un modèle basé sur les commandes et les événements, et éventuellement sur les messages asynchrones. Dans de nombreux cas, CQRS est lié à des scénarios plus avancés, comme disposer d’une base de données physique différente pour les lectures (requêtes) et pour les écritures (mises à jour). De plus, un système CQRS plus évolué peut implémenter la fonctionnalité d’[Event Sourcing ](https://martinfowler.com/eaaDev/EventSourcing.html) (approvisionnement d’événements) pour votre base de données de mises à jour, de sorte que vous ne stockez que les événements du modèle de domaine au lieu de stocker les données d’état actuel. Toutefois, cette approche n’est pas utilisée dans ce guide. Ce guide utilise l’approche CQRS la plus simple, qui consiste simplement à séparer les requêtes des commandes.

L’aspect de séparation de CQRS est obtenu en regroupant les opérations de requête dans une couche et les commandes dans une autre couche. Chaque couche a son propre modèle de données (notez que nous disons « modèle », pas nécessairement une base de données différente) et est construite à l’aide de sa propre combinaison de modèles et de technologies. Plus important encore, les deux couches peuvent se trouver dans le même niveau ou microservice, comme dans l’exemple (microservice de commandes) utilisé dans ce guide. Elles peuvent également être implémentées sur des microservices ou processus différents afin de pouvoir être optimisées et adaptées séparément sans s’affecter mutuellement.

CQRS implique d’avoir deux objets pour une opération de lecture/écriture où, dans d’autres contextes, il y en a un. Il existe des raisons d’avoir une base de données de lectures dénormalisée, sur laquelle vous pouvez obtenir des informations dans une documentation CQRS plus avancée. Mais nous n’utilisons pas cette approche ici, où l’objectif est d’avoir plus de souplesse dans les requêtes, et non pas de limiter les requêtes avec des contraintes à partir de modèles DDD comme les agrégats.

Il peut s’agir, par exemple, du microservice de commandes de l’application de référence eShopOnContainers. Ce service implémente un microservice basé sur une approche CQRS simplifiée. Il utilise une seule source de données ou base de données, mais deux modèles logiques plus des modèles DDD pour le domaine transactionnel, comme illustré dans la figure 7-2.

![Diagramme montrant un microservice global CQRS et DDD de haut niveau.](./media/apply-simplified-microservice-cqrs-ddd-patterns/simplified-cqrs-ddd-microservice.png)

**Figure 7-2**. Microservice basé sur les modèles CQRS et DDD simplifiés

Le microservice logique « ordonnancement » comprend sa base de données de tri, qui peut être, mais n’a pas besoin d’être, le même hôte d’ancrage. Le fait d’avoir la base de données dans le même hôte Docker est parfait pour le développement, mais pas pour la production.

La couche Application peut être l’API web elle-même. Ici, l’aspect important de la conception est que le microservice a séparé les requêtes et les ViewModels (modèles de données spécialement créés pour les applications clientes) des commandes, du modèle de domaine et des transactions suivant le modèle CQRS. Avec cette approche, les requêtes restent indépendantes des restrictions et des contraintes provenant de modèles DDD qui conviennent uniquement pour les transactions et les mises à jour, comme expliqué dans des sections ultérieures.

## <a name="additional-resources"></a>Ressources supplémentaires

- **Greg Young. Contrôle de version dans un système de source d’événements** (gratuit pour lire le livre électronique en ligne) \
   <https://leanpub.com/esversioning/read>

>[!div class="step-by-step"]
>[Précédent](index.md) 
> [Suivant](eshoponcontainers-cqrs-ddd-microservice.md)
