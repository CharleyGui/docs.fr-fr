---
title: Base de données par microservice
description: Stockage de données contrasté dans les applications monolithiques et cloud-natives.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: c0c5611fa866d70f155e4bdad2eee1181b13c065
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141443"
---
# <a name="database-per-microservice"></a>Base de données par microservice

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Comme nous l’avons vu tout au long de ce livre, une approche cloud-native change la façon dont vous concevez, déployez et gérez les applications. Il modifie également la façon dont vous gérez et stockez les données.

La figure 5-1 contraste avec les différences.

![Stockage de données dans les applications cloud-native](./media/distributed-data.png)

**Figure 5-1**. Gestion des données dans les applications cloud-native

Les développeurs expérimentés reconnaîtront facilement l’architecture sur le côté gauche de la figure 5-1. Dans cette *application monolithique,* les composants de services d’affaires se regroupent dans un niveau de services partagés, partageant les données d’une seule base de données relationnelle.

À bien des égards, une seule base de données permet de simplifier la gestion des données. Il est simple de poser des données sur plusieurs tableaux. Modifications apportées à la mise à jour des données ensemble ou elles sont toutes en recul. [Les transactions ACID](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) garantissent une cohérence forte et immédiate.

Concevoir pour le cloud-native, nous adoptons une approche différente. Sur le côté droit de la figure 5-1, notez comment la fonctionnalité des entreprises se sépare en petits microservices indépendants. Chaque microservice encapsule une capacité d’entreprise spécifique et ses propres données. La base de données monolithique se décompose en un modèle de données distribués avec de nombreuses bases de données plus petites, chacune s’alignant sur un microservice. Lorsque la fumée s’éclaircit, nous émergeons avec un design qui expose une *base de données par microservice.*

## <a name="why"></a>Pourquoi ?

Cette base de données par microservice offre de nombreux avantages, en particulier pour les systèmes qui doivent évoluer rapidement et soutenir l’échelle massive. Avec ce modèle...

- Les données de domaine sont encapsulées au sein du service
- Le schéma de données peut évoluer sans avoir d’impact direct sur d’autres services
- Chaque magasin de données peut évoluer de façon indépendante
- Une défaillance d’un magasin de données dans un service n’aura pas d’impact direct sur d’autres services

La séparation des données permet également à chaque microservice de mettre en œuvre le type de magasin de données qui est le mieux optimisé pour sa charge de travail, ses besoins de stockage et ses modèles de lecture et d’écriture. Les choix comprennent des magasins de données relationnels, documentaires, de valeur clé et même graphiques.

La figure 5-2 présente le principe de la persistance polyglotte dans un système nébuleux.

![Persistance des données polyglotte](./media/polyglot-data-persistence.png)

**Figure 5-2**. Persistance des données polyglotte

Notez dans le chiffre précédent comment chaque microservice prend en charge un type différent de magasin de données.

- Le microservice de catalogue de produits consomme une base de données relationnelle pour s’adapter à la riche structure relationnelle de ses données sous-jacentes.
- Le microservice de panier consomme un cache distribué qui prend en charge son magasin de données simple et de valeur clé.
- Le microservice de commande consomme à la fois une base de données de documents NoSql pour les opérations d’écriture ainsi qu’un magasin de clés/valeur hautement dénormalisé pour accueillir des volumes élevés d’opérations de lecture.
  
Bien que les bases de données relationnelles demeurent pertinentes pour les microservices avec des données complexes, les bases de données NoSQL ont gagné en popularité. Ils fournissent une grande échelle et une grande disponibilité. Leur nature sans schéma permet aux développeurs de s’éloigner d’une architecture de classes de données typées et de OUM qui rendent le changement coûteux et long. Nous couvrons les bases de données NoSQL plus tard dans ce chapitre.

 Bien que l’encapsulation des données en microservices distincts puisse accroître l’agilité, les performances et l’évolutivité, elles présentent également de nombreux défis. Dans la section suivante, nous discutons de ces défis ainsi que des modèles et des pratiques pour aider à les surmonter.  

## <a name="cross-service-queries"></a>Requêtes inter-services

Bien que les microservices soient indépendants et se concentrent sur des capacités fonctionnelles spécifiques, comme l’inventaire, l’expédition ou la commande, ils nécessitent souvent une intégration avec d’autres microservices. Souvent, l’intégration implique un microservice *interrogeant* un autre pour les données. La figure 5-3 montre le scénario.

![Interroger les microservices](./media/cross-service-query.png)

**Figure 5-3**. Interroger les microservices

Dans le chiffre précédent, nous voyons un microservice de panier d’achat qui ajoute un article au panier d’un utilisateur. Bien que le magasin de données pour ce microservice contienne des données sur les paniers et les éléments de ligne, il ne conserve pas les données sur les produits ou les prix. Au lieu de cela, ces éléments de données sont la propriété du catalogue et des microservices de prix. Cela pose un problème. Comment le microservice du panier d’achat peut-il ajouter un produit au panier d’achat de l’utilisateur lorsqu’il n’a pas de produit ni de données de tarification dans sa base de données ?

Une option discutée dans le chapitre 4 est un [appel HTTP direct](service-to-service-communication.md#queries) du panier d’achat au catalogue et aux microservices de tarification. Cependant, dans le chapitre 4, nous avons dit synchrone HTTP appelle les microservices *couples* ensemble, réduisant leur autonomie et diminuant leurs avantages architecturaux.

Nous pourrions également mettre en œuvre un modèle de demande-réponse avec des files d’attente à l’arrivée et à l’étranger séparées pour chaque service. Cependant, ce modèle est compliqué et exige la plomberie pour corréler les messages de demande et de réponse.
Bien qu’il ne découpler les appels de microservice backend, le service d’appel doit toujours attendre avec synchronité pour l’appel à remplir. La congestion du réseau, les défauts transitoires ou un microservice surchargé peuvent entraîner des opérations de longue durée et même défectueuses.

Au lieu de cela, un modèle largement accepté pour supprimer les dépendances inter-services est le [modèle de vue matérialisé](https://docs.microsoft.com/azure/architecture/patterns/materialized-view), indiqué dans la figure 5-4.

![Modèle de vue matérialisé](./media/materialized-view-pattern.png)

**Figure 5-4**. Modèle de vue matérialisé

Avec ce modèle, vous placez une table de données locale (connue sous le nom de *modèle de lecture*) dans le service de panier d’achat. Ce tableau contient une copie dénormalisée des données nécessaires à partir des microservices du produit et des prix. Copier les données directement dans le microservice du panier d’achat élimine le besoin d’appels interservices coûteux. Avec les données locales au service, vous améliorez le temps de réponse et la fiabilité du service. En outre, avoir sa propre copie des données rend le service de panier d’achat plus résilient. Si le service de catalogue devenait indisponible, il n’aurait pas d’impact direct sur le service de paniers d’achat. Le panier d’achat peut continuer à fonctionner avec les données de son propre magasin.

Le hic avec cette approche est que vous avez maintenant des données en double dans votre système. Cependant, le dupliquer *stratégiquement* les données dans les systèmes cloud-autochtones est une pratique établie et non considérée comme un anti-modèle, ou une mauvaise pratique. Gardez à *l’esprit qu’un seul et unique service* peut posséder un ensemble de données et avoir autorité sur celui-ci. Vous devrez synchroniser les modèles de lecture lorsque le système d’enregistrement est mis à jour. La synchronisation est généralement implémentée par messagerie asynchrone avec un [modèle de publication/abonné,](service-to-service-communication.md#events)comme le montre la figure 5.4.

## <a name="distributed-transactions"></a>Transactions distribuées

Bien qu’il soit difficile de interroger des données dans les microservices, la mise en œuvre d’une transaction dans plusieurs microservices est encore plus complexe. Le défi inhérent au maintien de la cohérence des données entre les sources de données indépendantes dans différents microservices ne peut être sous-estimé. L’absence de transactions distribuées dans les applications cloud-native signifie que vous devez gérer les transactions distribuées de manière programmatique. Vous passez d’un monde de *cohérence immédiate* à celui de *la cohérence éventuelle.*

La figure 5-5 montre le problème.

![Transaction en saga](./media/saga-transaction-operation.png)

**Figure 5-5**. Mise en œuvre d’une transaction entre microservices

Dans le chiffre précédent, cinq microservices indépendants participent à une transaction distribuée qui crée une commande. Chaque microservice tient son propre magasin de données et met en œuvre une transaction locale pour son magasin. Pour créer l’ordre, la transaction locale pour *chaque* microservice individuel doit réussir, ou *tous* doivent interrompre et annuler l’opération. Bien que le support transactionnel intégré soit disponible à l’intérieur de chacun des microservices, il n’y a aucun support pour une transaction distribuée qui s’étendrait sur les cinq services pour maintenir les données cohérentes.

Au lieu de cela, vous devez construire cette transaction distribuée *programmatiquement*.

Un modèle populaire pour ajouter le support transactionnel distribué est le modèle Saga. Il est mis en œuvre en groupant les transactions locales ensemble programmatiquement et séquentiellement invoquant chacune d’elles. Si l’une des transactions locales échoue, la Saga annule l’opération et invoque un ensemble de [transactions compensatoires](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction). Les transactions compensatoires annulent les modifications apportées par les transactions locales précédentes et rétablissent l’uniformité des données. La figure 5-6 montre une transaction ratée avec le modèle Saga.

![Retour en arrière dans le modèle de saga](./media/saga-rollback-operation.png)

**Figure 5-6**. Restauration d’une transaction

Dans le chiffre précédent, l’opération *d’inventaire de mise à jour* a échoué dans le microservice d’inventaire. La Saga invoque un ensemble de transactions compensatoires (en rouge) pour ajuster le nombre d’inventaires, annuler le paiement et la commande, et renvoyer les données pour chaque microservice à un état cohérent.

Les motifs de saga sont généralement chorégraphiés comme une série d’événements connexes, ou orchestrés comme un ensemble de commandes connexes. Dans le chapitre 4, nous avons discuté du modèle d’agrégateur de services qui serait à la base d’une mise en œuvre orchestrée de saga. Nous avons également discuté de l’événementiel avec Azure Service Bus et Azure Event Grid sujets qui serait une base pour une mise en œuvre de saga chorégraphiée.

## <a name="high-volume-data"></a>Données à volume élevé

Les grandes applications cloud-native prennent souvent en charge les besoins de données à volume élevé. Dans ces scénarios, les techniques traditionnelles de stockage de données peuvent causer des goulots d’étranglement. Pour les systèmes complexes qui se déploient à grande échelle, la ségrégation des responsabilités de commandement et de requête (CQRS) et l’approvisionnement en événements peuvent améliorer le rendement de l’application.  

### <a name="cqrs"></a>CQRS

[CQRS](https://docs.microsoft.com/azure/architecture/patterns/cqrs), est un modèle architectural qui peut aider à maximiser les performances, l’évolutivité et la sécurité. Le modèle sépare les opérations qui lisent les données des opérations qui rédigent des données.

Pour les scénarios normaux, le même modèle d’entité et l’objet de dépôt de données sont utilisés pour *les* opérations de lecture et d’écriture.

Cependant, un scénario de données à volume élevé peut bénéficier de modèles distincts et de tableaux de données pour les lectures et les écrits. Pour améliorer les performances, l’opération de lecture pourrait s’interroger contre une représentation très dénormalisée des données afin d’éviter les jointures de table répétitives coûteuses et les serrures de table. *L’opération d’écriture,* connue sous le nom de *commande,* serait mise à jour contre une représentation entièrement normalisée des données qui garantirait la cohérence. Vous devez ensuite mettre en œuvre un mécanisme pour synchroniser les deux représentations. Typiquement, chaque fois que le tableau d’écriture est modifié, il publie un événement qui reproduit la modification à la table de lecture.

La figure 5-7 montre une mise en œuvre du modèle CQRS.

![Ségrégation de responsabilité de commandement et de requête](./media/cqrs-implementation.png)

**Figure 5-7**. Mise en œuvre du CQRS

Dans la figure précédente, des modèles distincts de commande et de requête sont implémenté. Chaque opération d’écriture de données est enregistrée dans le magasin d’écriture, puis propagée au magasin de lecture. Portez une attention particulière à la façon dont le processus de propagation des données fonctionne sur le principe de [cohérence éventuelle](http://www.cloudcomputingpatterns.org/eventual_consistency/). Le modèle de lecture finit par se synchroniser avec le modèle d’écriture, mais il peut y avoir un certain décalage dans le processus. Nous discutons de la cohérence éventuelle dans la section suivante.

Cette séparation permet de lire et d’écrire à l’échelle indépendamment. Lire les opérations utilisent un schéma optimisé pour les requêtes, tandis que les écrits utilisent un schéma optimisé pour les mises à jour. Lire les requêtes vont à l’encontre des données dénormalisées, tandis que la logique commerciale complexe peut être appliquée au modèle d’écriture. En outre, vous pourriez imposer une sécurité plus stricte sur les opérations d’écriture que ceux exposant des lectures.

La mise en œuvre de CQRS peut améliorer les performances d’application pour les services cloud-natives. Cependant, il en résulte une conception plus complexe. Appliquez ce principe avec soin et stratégiquement aux sections de votre application cloud-native qui en bénéficieront. Pour en savoir plus sur CQRS, voir le livre de Microsoft [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/apply-simplified-microservice-cqrs-ddd-patterns).

### <a name="event-sourcing"></a>Sourcing d’événements

Une autre approche pour optimiser les scénarios de données à volume élevé implique [Event Sourcing](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

Un système stocke généralement l’état actuel d’une entité de données. Si un utilisateur modifie son numéro de téléphone, par exemple, l’enregistrement du client est mis à jour avec le nouveau numéro. Nous connaissons toujours l’état actuel d’une entité de données, mais chaque mise à jour surcrit l’état précédent.

Dans la plupart des cas, ce modèle fonctionne très bien. Dans les systèmes à volume élevé, cependant, les frais généraux provenant des opérations de verrouillage transactionnel et de mise à jour fréquentes peuvent avoir une incidence sur les performances, la réactivité et la limite de l’évolutivité dans les bases de données.

Event Sourcing adopte une approche différente pour la saisie des données. Chaque opération qui affecte les données est persistée dans un magasin d’événements. Au lieu de mettre à jour l’état d’un dossier de données, nous appendicons chaque modification à une liste séquentielle d’événements passés - semblable au registre d’un comptable. Le Magasin d’événements devient le système d’enregistrement des données. Il est utilisé pour propager diverses vues matérialisées dans le contexte délimité d’un microservice. La figure 5.8 montre le modèle.

![Approvisionnement en événements](./media/event-sourcing.png)

**Figure 5-8**. Approvisionnement en événements

Dans le chiffre précédent, notez comment chaque entrée (en bleu) pour le panier d’achat d’un utilisateur est annexée à un magasin d’événements sous-jacent. Dans la vue matérialisée adjacente, le système projette l’état actuel en rejouant tous les événements associés à chaque panier. Cette vue, ou modèle de lecture, est ensuite exposée à l’interface utilisateur. Les événements peuvent également être intégrés avec des systèmes et des applications externes ou interrogés pour déterminer l’état actuel d’une entité. Avec cette approche, vous maintenez l’histoire. Vous savez non seulement l’état actuel d’une entité, mais aussi comment vous avez atteint cet état.

Mécaniquement parlant, l’approvisionnement en événements simplifie le modèle d’écriture. Il n’y a pas de mises à jour ou de suppressions. L’absorption de chaque saisie de données comme un événement immuable minimise les conflits de contention, de verrouillage et de concurrence associés aux bases de données relationnelles. Construire des modèles de lecture avec le modèle de vue matérialisé vous permet de découpler la vue du modèle d’écriture et de choisir le meilleur magasin de données pour optimiser les besoins de votre interface utilisateur d’application.

Pour ce modèle, envisagez un magasin de données qui prend directement en charge l’approvisionnement en événements. Azure Cosmos DB, MongoDB, Cassandra, CouchDB et RavenDB sont de bons candidats.

Comme pour tous les modèles et toutes les technologies, implémenter stratégiquement et en cas de besoin. Bien que l’approvisionnement en événements puisse offrir une performance et une évolutivité accrues, il se fait au détriment de la complexité et d’une courbe d’apprentissage.

>[!div class="step-by-step"]
>[Suivant précédent](service-mesh-communication-infrastructure.md)
>[Next](relational-vs-nosql-data.md)
