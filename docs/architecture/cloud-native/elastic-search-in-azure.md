---
title: Elasticsearch dans les applications cloud-native
description: Découvrez l’ajout de capacités de recherche élastique aux applications cloud-natives.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 1bce255b6315006b11e0b6ac77040300f67ed984
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141287"
---
# <a name="elasticsearch-in-a-cloud-native-app"></a>Elasticsearch dans une application cloud-native

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Elasticsearch est un système de recherche et d’analyse distribué qui permet des capacités de recherche complexes à travers divers types de données. Il est open source et très populaire. Considérez comment les entreprises suivantes intègrent Elasticsearch dans leur application :

- [Wikipédia](https://blog.wikimedia.org/2014/01/06/wikimedia-moving-to-elasticsearch/) pour le texte intégral et la recherche incrémentale (recherche que vous tapez).
- [GitHub](https://www.elastic.co/customers/github) pour indexer et exposer plus de 8 millions de dépôts de code.  
- [Docker](https://www.elastic.co/customers/docker) pour rendre sa bibliothèque de conteneurs détectable.

Elasticsearch est construit sur le moteur de recherche à texte complet [Apache Lucene.](https://lucene.apache.org/core/) Lucene fournit l’indexation et la requête de documents haute performance. Il indexe les données avec un système d’indexation inversé - au lieu de cartographier les pages à des mots clés, il cartographie les mots clés à des pages comme un glossaire à la fin d’un livre. Lucene a de puissantes capacités de syntaxe de requête et peut interroger les données en :

- Terme (un mot complet)
- Préfixe (commence-avec mot)
- Wildcard (à\*l’aide de filtres " ou " ? "
- Phrase (une séquence de texte dans un document)
- Valeur Boolean (recherches complexes combinant requêtes)

Alors que Lucene fournit une plomberie de bas niveau pour la recherche, Elasticsearch fournit le serveur qui se trouve au-dessus de Lucene. Elasticsearch ajoute des fonctionnalités de plus haut niveau pour simplifier le travail Lucene, y compris une API RESTful pour accéder à la fonctionnalité d’indexation et de recherche de Lucene. Il fournit également une infrastructure distribuée capable d’évolutivité massive, de tolérance aux défauts et d’une grande disponibilité.

Pour les applications cloud-natives plus grandes avec des besoins de recherche complexes, Elasticsearch est disponible en tant que service géré en Azure. Le Microsoft Azure Marketplace propose des modèles préconfigurés que les développeurs peuvent utiliser pour déployer un cluster Elasticsearch sur Azure.

Depuis Microsoft Azure Marketplace, les développeurs peuvent utiliser des modèles préconfigurés conçus pour déployer rapidement un cluster Elasticsearch sur Azure. Grâce à l’offre gérée par Azure, vous pouvez déployer jusqu’à 50 nœuds de données, 20 nœuds de coordination et trois nœuds maîtres dédiés.

## <a name="summary"></a>Résumé

Ce chapitre a présenté un regard détaillé sur les données des systèmes cloud-autochtones. Nous avons commencé par contraster le stockage de données dans des applications monolithiques avec des modèles de stockage de données dans les systèmes cloud-natifs. Nous avons examiné les modèles de données mis en œuvre dans les systèmes natifs du cloud, y compris les requêtes inter-services, les transactions distribuées et les modèles pour traiter les systèmes à volume élevé. Nous avons contrasté SQL avec les données NoSQL. Nous avons examiné les options de stockage de données disponibles dans Azure qui incluent à la fois des options microsoft-centriques et open-source. Enfin, nous avons discuté de la mise en cache et de l’elasticsearch dans une application cloud-native.

### <a name="references"></a>References

- [Modèle de séparation des responsabilités en matière de commande et de requête (CQRS)](https://docs.microsoft.com/azure/architecture/patterns/cqrs)

- [Modèle d'approvisionnement en événements](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)

- [RDBMS vs Bases de données NoSQL : Aperçu](https://maxivak.com/rdbms-vs-nosql-databases/)

- [Pourquoi la partition RDBMS n’est-elle pas tolérante dans le théorème cap et pourquoi est-elle disponible ?](https://stackoverflow.com/questions/36404765/why-isnt-rdbms-partition-tolerant-in-cap-theorem-and-why-is-it-available)

- [Vue matérialisée](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

- [Tout ce que vous devez vraiment savoir sur les bases de données open source](https://www.ibm.com/blogs/systems/all-you-really-need-to-know-about-open-source-databases/)

- [Modèle de transaction de compensation](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Modèle de saga](https://microservices.io/patterns/data/saga.html)

- [Modèles saga Comment mettre en œuvre les transactions commerciales à l’aide de microservices](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/)

- [Modèle de transaction de compensation](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)

- [Se mettre derrière le 9-Ball: Cosmos DB niveaux de cohérence expliqué](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/)

- [Explorer les différents types de bases de données NoSQL Partie II](https://www.3pillarglobal.com/insights/exploring-the-different-types-of-nosql-databases)

- [Sur les bases de données RDBMS, NoSQL et NewSQL. Entrevue avec John Ryan](http://www.odbms.org/blog/2018/03/on-rdbms-nosql-and-newsql-databases-interview-with-john-ryan/)
  
- [SQL vs NoSQL vs NewSQL: La comparaison complète](https://www.xenonstack.com/blog/sql-vs-nosql-vs-newsql/)

- [DASH: Quatre propriétés de bases de données Kubernetes-Native](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

- [CafardDB](https://www.cockroachlabs.com/)

- [TiDB (TiDB)](https://pingcap.com/en/)

- [YugabyteDB](https://www.yugabyte.com/)

- [Vitess Vitess](https://vitess.io/)

- [Elasticsearch: The Definitive Guide (Elasticsearch : le guide de référence)](http://shop.oreilly.com/product/0636920028505.do)
  
- [Introduction à Apache Lucene](https://www.baeldung.com/lucene)

>[!div class="step-by-step"]
>[Suivant précédent](azure-caching.md)
>[Next](resiliency.md) <!-- Next Chapter -->
