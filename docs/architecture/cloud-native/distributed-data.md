---
title: Données distribuées
description: Le contraste du stockage des données dans les applications monolithiques et Cloud natives.
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 28513f8691c06cf58ed14d57bf7830bb35d94852
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144394"
---
# <a name="distributed-data"></a>Données distribuées

Comme nous l’avons vu dans ce livre, une approche Cloud-Native change la façon dont vous concevez, déployez et gérez les applications. Il modifie également la façon dont vous gérez et stockez les données.

La figure 5-1 compare les différences.

![Stockage des données dans les applications natives du Cloud](./media/distributed-data.png)

**Figure 5-1**. Gestion des données dans les applications Cloud natives

Les développeurs expérimentés reconnaîtront facilement l’architecture sur le côté gauche de la figure 5-1. Dans cette *application monolithique*, les composants de service métier colocaliser ensemble dans un niveau de services partagés, en partageant des données à partir d’une base de données relationnelle unique.

À bien des égards, une seule base de données conserve la gestion des données simple. L’interrogation de données entre plusieurs tables est simple. Modifications apportées à la mise à jour des données ensemble ou restauration. Les [transactions ACID](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) garantissent une cohérence forte et immédiate.

En concevant pour le Cloud natif, nous prenons une approche différente. Dans la partie droite de la figure 5-1, notez la manière dont les fonctionnalités métier sont séparées en microservices indépendants et petits. Chaque microservice encapsule une fonctionnalité métier spécifique et ses propres données. La base de données monolithique est décomposée en un modèle de données distribué avec de nombreuses bases de données plus petites, chacune correspondant à un microservice. Lorsque la fumée disparaît, nous avons découvert une conception qui expose une *base de données par Microservice*.

## <a name="database-per-microservice-why"></a>Base de données par Microservice, pourquoi ?

Cette base de données par Microservice offre de nombreux avantages, en particulier pour les systèmes qui doivent évoluer rapidement et prendre en charge une grande échelle. Avec ce modèle...

- Les données de domaine sont encapsulées dans le service
- Le schéma de données peut évoluer sans affecter directement les autres services
- Chaque magasin de données peut être mis à l’échelle indépendamment
- Une défaillance du magasin de données dans un service n’affecte pas directement les autres services

Le fait de séparer les données permet également à chaque microservice d’implémenter le type de magasin de données optimisé pour la charge de travail, les besoins de stockage et les modèles de lecture/écriture. Les choix sont les suivants : relationnel, document, clé-valeur et même magasins de données basés sur les graphiques.

La figure 5-2 présente le principe de la persistance polyglotte dans un système Cloud natif.

![Persistance des données polyglotte](./media/polyglot-data-persistence.png)

**Figure 5-2**. Persistance des données polyglotte

Notez dans la figure précédente comment chaque microservice prend en charge un type de magasin de données différent.

- Le microservice de catalogue de produits consomme une base de données relationnelle pour s’adapter à la structure relationnelle enrichie de ses données sous-jacentes.
- Le microservice panier d’achat consomme un cache distribué qui prend en charge sa propre banque de données de clé-valeur.
- Le microservice de commande consomme à la fois une base de données de documents NoSql pour les opérations d’écriture et un magasin de clés/valeurs très dénormalisé pour prendre en charge des volumes élevés d’opérations de lecture.
  
Si les bases de données relationnelles restent pertinentes pour les microservices avec des données complexes, les bases de données NoSQL ont gagné en popularité. Ils fournissent une mise à l’échelle et une haute disponibilité à grande échelle. Leur nature sans schéma permet aux développeurs de quitter une architecture de classes de données typées et de ORM, ce qui rend la modification coûteuse et fastidieuse. Nous abordons les bases de données NoSQL plus loin dans ce chapitre.

 L’encapsulation des données dans des microservices distincts peut accroître l’agilité, les performances et l’évolutivité, mais elle présente également de nombreux défis. Dans la section suivante, nous aborderons ces défis, ainsi que les modèles et les pratiques qui vous aideront à les surmonter.  

## <a name="cross-service-queries"></a>Requêtes entre services

Alors que les microservices sont indépendants et qu’ils se concentrent sur des fonctionnalités spécifiques, telles que l’inventaire, l’expédition ou l’ordonnancement, ils requièrent souvent une intégration avec d’autres microservices. L’intégration implique souvent l' *interrogation* d’un microservice pour les données. La figure 5-3 illustre le scénario.

![Interrogation sur des microservices](./media/cross-service-query.png)

**Figure 5-3**. Interrogation sur des microservices

Dans la figure précédente, nous voyons un microservice de panier d’achat qui ajoute un élément au panier d’achat d’un utilisateur. Alors que le magasin de données pour ce microservice contient des données de panier et d’élément de ligne, il ne conserve pas les données de produit ou de tarification. Au lieu de cela, ces éléments de données sont détenus par le catalogue et les microservices de tarification. Cela pose un problème. Comment le microservice du panier d’achat peut-il ajouter un produit au panier d’achat de l’utilisateur lorsqu’il n’a pas de données de produit ou de prix dans sa base de données ?

L’une des options présentées dans le chapitre 4 est un [appel http direct](service-to-service-communication.md#queries) du panier d’achat aux microservices de catalogue et de tarification. Toutefois, dans le chapitre 4, nous avons dit que les appels HTTP synchrones *couplent* les microservices ensemble, ce qui réduit leur autonomie et réduit leurs avantages architecturaux.

Nous pourrions également implémenter un modèle de demande-réponse avec des files d’attente entrantes et sortantes distinctes pour chaque service. Toutefois, ce modèle est complexe et nécessite la mise en corrélation des messages de demande et de réponse.
S’il dissocie les appels du microservice principal, le service appelant doit toujours attendre que l’appel se termine. La congestion du réseau, les erreurs temporaires ou un microservice surchargé et peuvent entraîner des opérations de longue durée et même en échec.

Au lieu de cela, un modèle largement accepté pour la suppression des dépendances entre les services est le [modèle de vue matérialisée](https://docs.microsoft.com/azure/architecture/patterns/materialized-view), illustré à la figure 5-4.

![Modèle de vue matérialisée](./media/materialized-view-pattern.png)

**Figure 5-4**. Modèle de vue matérialisée

Avec ce modèle, vous placez une table de données locale (appelée *modèle de lecture*) dans le service panier d’achat. Ce tableau contient une copie dénormalisée des données nécessaires à partir des microservices du produit et de la tarification. La copie des données directement dans le microservice du panier d’achat élimine le besoin d’appels interservice coûteux. Avec les données locales au service, vous améliorez le temps de réponse et la fiabilité du service. En outre, le fait de disposer de sa propre copie des données rend le service du panier d’achat plus résilient. Si le service de catalogue doit devenir indisponible, il n’a pas d’impact direct sur le service panier d’achat. Le panier d’achat peut continuer à fonctionner avec les données de son propre magasin.

Le piège avec cette approche est que vous avez maintenant des données en double dans votre système. Toutefois, la duplication *stratégique* des données dans les systèmes natifs du Cloud est une pratique établie et n’est pas considérée comme un anti-modèle ou une mauvaise pratique. N’oubliez pas qu' *un et un seul service* peuvent posséder un jeu de données et avoir une autorité sur celui-ci. Vous devez synchroniser les modèles de lecture lorsque le système d’enregistrement est mis à jour. La synchronisation est généralement implémentée via une messagerie asynchrone avec un [modèle de publication/abonnement](service-to-service-communication.md#events), comme illustré dans la figure 5,4.

## <a name="distributed-transactions"></a>Transactions distribuées

Bien que l’interrogation des données entre les microservices soit difficile, l’implémentation d’une transaction sur plusieurs microservices est encore plus complexe. Le défi inhérent à la gestion de la cohérence des données entre des sources de données indépendantes dans des microservices différents ne peut pas être sous-état. Le manque de transactions distribuées dans les applications natives du Cloud signifie que vous devez gérer les transactions distribuées par programme. Vous passez d’un monde de *cohérence immédiate* à celle de *la cohérence éventuelle*.

La figure 5-5 illustre le problème.

![Transaction dans le modèle saga](./media/saga-transaction-operation.png)

**Figure 5-5**. Implémentation d’une transaction sur des microservices

Dans la figure précédente, cinq microservices indépendants participent à une transaction distribuée qui crée une commande. Chaque microservice gère son propre magasin de données et implémente une transaction locale pour son magasin. Pour créer la commande, la transaction locale pour *chaque* microservice individuel doit être effectuée, ou *toutes* doivent abandonner et annuler l’opération. Alors que la prise en charge des transactions intégrée est disponible dans chacun des microservices, il n’existe pas de prise en charge d’une transaction distribuée qui s’étend sur les cinq services pour assurer la cohérence des données.

Au lieu de cela, vous devez construire cette transaction distribuée *par programme*.

Un modèle répandu pour l’ajout de la prise en charge transactionnelle distribuée est le modèle saga. Elle est implémentée en regroupant les transactions locales ensemble par programmation et en appelant séquentiellement chacune. Si l’une des transactions locales échoue, le saga abandonne l’opération et appelle un ensemble de [transactions de compensation](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction). Les transactions de compensation annulent les modifications apportées par les transactions locales précédentes et la cohérence des données de restauration. La figure 5-6 montre une transaction ayant échoué avec le modèle saga.

![Revenir en arrière dans le modèle saga](./media/saga-rollback-operation.png)

**Figure 5-6**. Restauration d’une transaction

Dans l’illustration précédente, l’opération de *mise à jour* de l’inventaire a échoué dans le microservice d’inventaire. Le saga appelle un ensemble de transactions de compensation (en rouge) pour ajuster le nombre d’inventaires, annuler le paiement et la commande et retourner les données pour chaque microservice dans un état cohérent.

Les modèles Saga sont généralement chorégraphiés sous la forme d’une série d’événements connexes, ou orchestrés sous la forme d’un ensemble de commandes associées. Dans le chapitre 4, nous avons abordé le modèle d’agrégation de services qui serait la base d’une implémentation saga orchestrée. Nous avons également abordé les événements, ainsi que les rubriques de Azure Service Bus et Azure Event Grid qui seraient la base d’une implémentation chorégraphiés saga.

## <a name="high-volume-data"></a>Données volumineuses

Les grandes applications Cloud natives prennent souvent en charge des exigences de données importantes. Dans ces scénarios, les techniques traditionnelles de stockage de données peuvent provoquer des goulots d’étranglement. Pour les systèmes complexes déployés à grande échelle, les séparation des responsabilités en matière de commande et de requête (CQRS) et l’approvisionnement des événements peuvent améliorer les performances de l’application.  

### <a name="cqrs"></a>CQRS

[CQRS](https://docs.microsoft.com/azure/architecture/patterns/cqrs)est un modèle architectural qui peut aider à optimiser les performances, l’évolutivité et la sécurité. Le modèle sépare les opérations qui lisent les données des opérations qui écrivent des données.

Pour les scénarios normaux, le même modèle d’entité et l’objet de référentiel de données sont utilisés pour *les* opérations de lecture et d’écriture.

Toutefois, un scénario de données volumineuses peut tirer parti de modèles et de tables de données distincts pour les lectures et les écritures. Pour améliorer les performances, l’opération de lecture peut interroger une représentation fortement dénormalisée des données afin d’éviter des jointures de tables et des verrous de table répétitifs coûteux. L’opération d' *écriture* , appelée *commande*, est mise à jour par rapport à une représentation entièrement normalisée des données qui garantissent la cohérence. Vous devez ensuite implémenter un mécanisme pour maintenir la synchronisation des deux représentations. En général, chaque fois que la table d’écriture est modifiée, elle publie un événement qui réplique la modification dans la table de lecture.

La figure 5-7 illustre une implémentation du modèle CQRS.

![séparation des responsabilités en matière de commande et de requête](./media/cqrs-implementation.png)

**Figure 5-7**. Implémentation CQRS

Dans la figure précédente, des modèles de commande et de requête distincts sont implémentés. Chaque opération d’écriture de données est enregistrée dans le magasin d’écriture, puis propagée vers le magasin de lecture. Portez une attention particulière à la façon dont le processus de propagation des données opère sur le principe de la [cohérence éventuelle](https://www.cloudcomputingpatterns.org/eventual_consistency/). Le modèle de lecture finit par se synchroniser avec le modèle d’écriture, mais il peut y avoir un décalage dans le processus. Nous aborderons la cohérence éventuelle dans la section suivante.

Cette séparation permet de mettre à l’échelle indépendamment les lectures et les écritures. Les opérations de lecture utilisent un schéma optimisé pour les requêtes, tandis que les écritures utilisent un schéma optimisé pour les mises à jour. Les requêtes de lecture dépassent les données dénormalisées, tandis que la logique métier complexe peut être appliquée au modèle d’écriture. En outre, vous pouvez imposer une sécurité plus étroite sur les opérations d’écriture que celles qui exposent des lectures.

L’implémentation de CQRS peut améliorer les performances des applications pour les services Cloud natifs. Toutefois, cela se traduit par une conception plus complexe. Appliquez ce principe avec soin et stratégiquement à ces sections de votre application Cloud native qui en tireront parti. Pour plus d’informations sur CQRS, consultez les [microservices .NET Microsoft Book : architecture pour les applications .net en conteneur](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/apply-simplified-microservice-cqrs-ddd-patterns).

### <a name="event-sourcing"></a>Provisionnement en événements

Une autre approche de l’optimisation des scénarios de données volumineuses implique l' [approvisionnement des événements](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

Un système stocke généralement l’état actuel d’une entité de données. Si un utilisateur modifie son numéro de téléphone, par exemple, l’enregistrement du client est mis à jour avec le nouveau numéro. Nous connaissons toujours l’état actuel d’une entité de données, mais chaque mise à jour remplace l’état précédent.

Dans la plupart des cas, ce modèle fonctionne correctement. Toutefois, dans les systèmes à volume élevé, la surcharge du verrouillage transactionnel et des opérations de mise à jour fréquentes peut avoir un impact sur les performances de la base de données, la réactivité et la limitation de l’évolutivité.

L’approvisionnement en événements adopte une approche différente pour la capture des données. Chaque opération qui affecte les données est conservée dans un magasin d’événements. Au lieu de mettre à jour l’état d’un enregistrement de données, nous avons ajouté chaque modification à une liste séquentielle d’événements passés, similaire à la comptabilité d’un comptable. Le magasin d’événements devient le système d’enregistrement des données. Elle est utilisée pour propager différentes vues matérialisées dans le contexte limité d’un microservice. La figure 5,8 illustre le modèle.

![Approvisionnement en événements](./media/event-sourcing.png)

**Figure 5-8**. Approvisionnement en événements

Dans la figure précédente, notez la manière dont chaque entrée (en bleu) du panier d’achat d’un utilisateur est ajoutée à un magasin d’événements sous-jacent. Dans la vue matérialisée adjacente, le système projette l’état actuel en relisant tous les événements associés à chaque panier. Cette vue, ou lire le modèle, est ensuite exposée à l’interface utilisateur. Les événements peuvent également être intégrés à des systèmes externes et à des applications, ou être interrogés pour déterminer l’état actuel d’une entité. Avec cette approche, vous conservez l’historique. Vous savez non seulement l’état actuel d’une entité, mais également comment vous avez atteint cet État.

En parlant mécanique, l’approvisionnement en événements simplifie le modèle d’écriture. Il n’y a aucune mise à jour ou suppression. L’ajout de chaque entrée de données comme un événement immuable minimise les conflits de contention, de verrouillage et d’accès concurrentiel associés aux bases de données relationnelles. La création de modèles de lecture avec le modèle de vue matérialisée vous permet de découpler la vue du modèle d’écriture et de choisir la meilleure banque de données pour optimiser les besoins de l’interface utilisateur de votre application.

Pour ce modèle, envisagez un magasin de données qui prend directement en charge l’approvisionnement des événements. Azure Cosmos DB, MongoDB, Cassandra, CouchDB et RavenDB sont de bons candidats.

Comme avec tous les modèles et technologies, implémentez stratégiquement et si nécessaire. Bien que l’approvisionnement en événements puisse offrir des performances et une évolutivité accrues, il est au détriment de la complexité et d’une courbe d’apprentissage.

>[!div class="step-by-step"]
>[Précédent](service-mesh-communication-infrastructure.md) 
> [Suivant](relational-vs-nosql-data.md)
