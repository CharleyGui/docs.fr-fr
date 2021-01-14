---
title: Application des approches CQRS et CQS dans un microservice DDD dans eShopOnContainers
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre la façon dont CQRS est implémenté dans le microservice Ordering de l’application eShopOnContainers.
ms.date: 01/13/2021
ms.openlocfilehash: 0c07ecad0fb2dfdaea85d47b519b858e0519f6bd
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188255"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>Appliquer des approches CQRS et CQS dans un microservice DDD dans eShopOnContainers

La conception du microservice de commandes au niveau de l’application de référence eShopOnContainers est basée sur les principes CQRS. Toutefois, elle utilise l’approche la plus simple, qui consiste simplement à séparer les requêtes des commandes et à utiliser la même base de données pour les deux actions.

Le concept essentiel de ces modèles, et le point important ici, est que les requêtes sont idempotentes : quel que soit le nombre de fois où vous interrogez un système, son état ne change pas. En d’autres termes, les requêtes n’ont pas d’effet secondaire.

Par conséquent, vous pouvez utiliser un modèle de données « lectures » différent du modèle de domaine « écritures » logique transactionnelle, même si les microservices de commande utilisent la même base de données. Il s’agit donc d’une approche CQRS simplifiée.

En revanche, les commandes qui déclenchent des transactions et mises à jour de données changent l’état du système. Avec les commandes, vous devez être prudent quand vous abordez le problème de la complexité et les règles métier en constante évolution. C’est là où vous souhaitez appliquer des techniques DDD pour obtenir un système mieux modélisé.

Les modèles DDD présentés dans ce guide ne doivent pas être appliqués de manière universelle. Ils introduisent des contraintes dans votre conception. Ces contraintes présentent des avantages, notamment une meilleure qualité au fil du temps, en particulier dans les commandes et tout code qui modifie l’état du système. Toutefois, ces contraintes augmentent la complexité avec moins d’avantages pour la lecture et l’interrogation des données.

Un modèle de ce type est le modèle Agrégat, que nous examinerons plus en détail dans les sections suivantes. Brièvement, dans le modèle Agrégat, vous traitez un grand nombre d’objets de domaine comme un seul ensemble en raison de leur relation dans le domaine. Il est possible que vous n’obteniez pas toujours des avantages avec ce modèle dans les requêtes, car celui-ci peut augmenter la complexité de la logique de requête. Pour les requêtes en lecture seule, vous n’obtenez pas les avantages de traitement de plusieurs objets comme un seul agrégat, juste la complexité.

Comme le montre la figure 7-2 de la section précédente, ce guide suggère l’utilisation de modèles DDD uniquement dans la zone transactionnelle/de mises à jour de votre microservice (autrement dit, tel qu’il est déclenché par des commandes). Les requêtes peuvent suivre une approche plus simple et doivent être séparées des commandes, suite à une approche CQRS.

Pour l’implémentation du côté « requêtes », vous pouvez choisir entre plusieurs approches, à partir de votre ORM complet, comme EF Core, les projections du Mappeur, les procédures stockées, les vues, les vues matérialisées ou un micro ORM.

Dans ce guide et dans eShopOnContainers (en particulier le microservice de commandes), nous avons choisi d’implémenter des requêtes simples à l’aide d’un micro-ORM comme [Dapper](https://github.com/StackExchange/dapper-dot-net). Ce guide vous permet d’implémenter n’importe quelle requête basée sur des instructions SQL pour obtenir des performances optimales grâce à une infrastructure légère avec peu de surcharge.

Lorsque vous utilisez cette approche, toutes les mises à jour de votre modèle qui ont un impact sur la façon dont les entités sont conservées dans une base de données SQL nécessitent également des mises à jour séparées pour les requêtes SQL utilisées par dapper ou toute autre approche distincte (non EF) pour l’interrogation.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>Les modèles CQRS et DDD ne sont pas des architectures de niveau supérieur

Il est important de comprendre que CQRS et la plupart des modèles DDD (comme les couches DDD ou un modèle de domaine avec des agrégats) ne sont pas des styles d’architecture, mais seulement des modèles d’architecture. Les microservices, SOA et l’architecture pilotée par événements (EDA) sont des exemples de styles architecturaux. Ils décrivent un système de nombreux composants, tels que de nombreux microservices. Les modèles CQRS et DDD décrivent un élément à l’intérieur d’un système ou composant unique, dans ce cas un élément à l’intérieur d’un microservice.

Des contextes délimités différents vont utiliser différents modèles. Ils ont des responsabilités diverses, ce qui aboutit à différentes solutions. Il est important de souligner que le fait d’imposer le même modèle partout entraîne un échec. N’utilisez pas les modèles CQRS et DDD partout. De nombreux sous-systèmes, contextes délimités ou microservices sont plus simples et peuvent être implémentés plus facilement à l’aide de services CRUD de base ou d’une autre approche.

Il n’existe qu’une seule architecture des applications : l’architecture de l’application système ou de bout en bout que vous concevez (par exemple, l’architecture de microservices). Toutefois, la conception de chaque contexte délimité ou microservice au sein de cette application reflète ses propres compromis et décisions de conception interne à un niveau de modèles d’architecture. N’essayez pas d’appliquer les mêmes modèles d’architecture que CQRS ou DDD partout.

### <a name="additional-resources"></a>Ressources supplémentaires

- **Martin Fowler. CQRS** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Greg Young. Documents CQRS** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf>

- **UDI Dahan. CQRS clarifié** \
  <https://udidahan.com/2009/12/09/clarified-cqrs/>

>[!div class="step-by-step"]
>[Précédent](apply-simplified-microservice-cqrs-ddd-patterns.md) 
> [Suivant](cqrs-microservice-reads.md)
