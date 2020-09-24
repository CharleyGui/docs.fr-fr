---
title: Elasticsearch dans les applications Cloud natives
description: En savoir plus sur l’ajout de fonctionnalités de recherche élastique aux applications Cloud natives.
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: fa46f3387eecb3fccd63fdea10c11e92923ae862
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155378"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a>Elasticsearch dans une application Cloud Native

Elasticsearch est un système de recherche et d’analyse distribué qui permet des fonctionnalités de recherche complexes sur divers types de données. Il est open source et largement populaire. Prenez en compte la façon dont les entreprises suivantes intègrent Elasticsearch dans leur application :

- Recherche de texte intégral et de recherche incrémentielle (recherche au fur [et à mesure](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) que vous tapez).
- [GitHub](https://www.elastic.co/customers/github) pour indexer et exposer plus de 8 millions référentiels de code.  
- [Ancrer](https://www.elastic.co/customers/docker) pour rendre sa bibliothèque de conteneurs détectable.

Elasticsearch repose sur le moteur de recherche en texte intégral [Apache Lucene](https://lucene.apache.org/core/) . Lucene fournit l’indexation et l’interrogation de documents à hautes performances. Il indexe les données avec un schéma d’indexation inversé : au lieu de mapper les pages aux mots clés, il mappe les mots clés aux pages comme un glossaire à la fin d’un livre. Lucene dispose de puissantes fonctionnalités de syntaxe de requête et peut interroger les données de la façon suivante :

- Terme (un mot complet)
- Préfixe (commençant par Word)
- Caractère générique (à l’aide des \* filtres « » ou « ? »)
- Expression (une séquence de texte dans un document)
- Valeur booléenne (recherches complexes combinant des requêtes)

Bien que Lucene fournisse des éléments de bas niveau pour la recherche, Elasticsearch fournit le serveur qui se trouve au-dessus de Lucene. Elasticsearch ajoute des fonctionnalités de niveau supérieur pour simplifier le travail Lucene, y compris une API RESTful pour accéder aux fonctionnalités d’indexation et de recherche de Lucene. Il fournit également une infrastructure distribuée, capable d’évoluer massivement, de tolérance de panne et de haute disponibilité.

Pour les applications Cloud plus volumineuses avec des exigences de recherche complexes, Elasticsearch est disponible en tant que service géré dans Azure. Le Place de marché Microsoft Azure propose des modèles préconfigurés que les développeurs peuvent utiliser pour déployer un cluster Elasticsearch sur Azure.

Du Place de marché Microsoft Azure, les développeurs peuvent utiliser des modèles préconfigurés pour déployer rapidement un cluster Elasticsearch sur Azure. À l’aide de l’offre gérée par Azure, vous pouvez déployer jusqu’à 50 nœuds de données, 20 nœuds de coordination et trois nœuds principaux dédiés.

## <a name="summary"></a>Résumé

Ce chapitre a présenté une vue détaillée des données dans les systèmes Cloud natifs. Nous avons commencé par comparer le stockage des données dans les applications monolithiques avec les modèles de stockage des données dans les systèmes natifs du Cloud. Nous avons examiné les modèles de données implémentés dans les systèmes Cloud natifs, notamment les requêtes entre services, les transactions distribuées et les modèles pour gérer les systèmes à volume élevé. Nous avons comparé SQL avec les données NoSQL. Nous avons examiné les options de stockage de données disponibles dans Azure qui incluent des options orientées Microsoft et open source. Enfin, nous avons abordé Caching et Elasticsearch dans une application Cloud native.

### <a name="references"></a>Références

- [Modèle séparation des responsabilités en matière de commande et de requête (CQRS)](/azure/architecture/patterns/cqrs)

- [Modèle d’approvisionnement en événements](/azure/architecture/patterns/event-sourcing)

- [Pourquoi la partition de SGBDR n’est-elle pas tolérante dans le CAP CAP et pourquoi est-elle disponible ?](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [Vue matérialisée](/azure/architecture/patterns/materialized-view)

- [Tout ce que vous devez savoir sur les bases de données Open source](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [Modèle de transaction de compensation](/azure/architecture/patterns/compensating-transaction)

- [Modèle saga](https://microservices.io/patterns/data/saga.html)

- [Modèles saga | Comment implémenter des transactions commerciales à l’aide de microservices](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [Modèle de transaction de compensation](/azure/architecture/patterns/compensating-transaction)

- [En arrière-plan des niveaux de cohérence 9 Ball : Cosmos DB expliqués](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [Exploration des différents types de bases de données NoSQL, partie II](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [Sur les bases de données de SGBDR, NoSQL et NewSQL. Entretien avec John Ryan](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [SQL vs NoSQL vs NewSQL : comparaison complète](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [DASH : quatre propriétés des bases de données Kubernetes-natives](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [CockroachDB](https://www.cockroachlabs.com/)

- [TiDB](https://pingcap.com/en/)

- [YugabyteDB](https://www.yugabyte.com/)

- [Vitess](https://vitess.io/)

- [Elasticsearch: The Definitive Guide (Elasticsearch : le guide de référence)](https://shop.oreilly.com/product/0636920028505.do)
  
- [Présentation d’Apache Lucene](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
>[Précédent](azure-caching.md) 
> [Suivant](resiliency.md) <!-- Next Chapter -->
