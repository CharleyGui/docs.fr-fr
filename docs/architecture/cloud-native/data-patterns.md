---
title: Modèles de données cloud natifs
description: Architecture des applications .NET natives Cloud pour Azure | Modèles de données natifs du Cloud
ms.date: 06/30/2019
ms.openlocfilehash: 0d251f3046fcd3f3a2f5d856a123a35d3f7ecff2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087698"
---
# <a name="cloud-native-data-patterns"></a>Modèles de données cloud natifs

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Si les données décentralisées peuvent améliorer les performances, l’évolutivité et les économies, elles présentent également de nombreux défis. L’interrogation des données entre les microservices est complexe. Une transaction qui s’étend sur les microservices doit être gérée par programmation, car les transactions distribuées ne sont pas prises en charge dans les applications natives du Cloud. Vous passez d’un monde de *cohérence immédiate* à *la cohérence éventuelle*.

Nous aborderons ces défis maintenant.

## <a name="cross-service-queries"></a>Requêtes entre services

Comment une application interroge-t-elle les données qui sont réparties sur plusieurs microservices indépendants ?

La figure 5-4 illustre ce scénario.

![Interrogation sur des microservices](./media/cross-service-query.png)

**Figure 5-4**. Interrogation sur des microservices

Notez comment, dans la figure précédente, nous voyons un microservice de panier d’achat qui ajoute un élément au panier d’achat d’un utilisateur. Alors que le magasin de données du panier d’achat contient une table basket et lineItem, il ne contient pas de données de produit ou de tarification, car ces éléments se trouvent dans les microservices Product et Price. Pour ajouter un élément, le microservice du panier d’achat a besoin des données de produit et de tarification. Quelles sont les options permettant d’obtenir le produit et les données de tarification ?

La figure 5-5 montre le microservice du panier d’achat qui effectue un appel HTTP direct au catalogue de produits et aux microservices de tarification.

![Communication http directe](./media/direct-http-communication.png)

**Figure 5-5**. Communication HTTP directe

Tout en réalisant l’implémentation, dans le chapitre 4, nous avons abordé la manière dont les appels HTTP directs entre les microservices couplent le système et ne sont pas considérés comme une bonne pratique.

Nous pourrions implémenter un microservice d’agrégation illustré à la figure 5-6.

![Microservice de l’agrégateur](./media/aggregator-microservice.png)

**Figure 5-6.** Microservice de l’agrégateur

Bien que cette approche encapsule le flux de travail de l’opération d’entreprise dans un microservice individuel, elle ajoute de la complexité et entraîne toujours des appels HTTP directs.

Une approche courante pour l’exécution de requêtes entre services utilise le [modèle de vue matérialisée](https://docs.microsoft.com/azure/architecture/patterns/materialized-view), illustré à la figure 5-7.

![Modèle de vue matérialisée](./media/materialized-view-pattern.png)

**Figure5-7**. Modèle de vue matérialisée

Avec ce modèle, vous placez directement une table locale (appelée modèle de *lecture*) dans le service panier d’achat qui contient une copie dénormalisée des données nécessaires à partir des microservices de produit et de tarification. Le placement de ces données dans le microservice du panier d’achat élimine la nécessité d’appeler des appels inter-services onéreux. Avec les données locales au service, vous améliorez le temps de réponse et la fiabilité.

La capture avec cette approche vous offre maintenant des données dupliquées dans votre système. Dans les systèmes Cloud natifs, les données dupliquées ne sont pas considérées comme un [anti-modèle](https://en.wikipedia.org/wiki/Anti-pattern) et sont généralement implémentées dans les systèmes natifs du Cloud. Toutefois, un seul système peut être propriétaire d’un jeu de données, et vous devez implémenter un mécanisme de synchronisation pour le système d’enregistrement afin de mettre à jour tous les modèles de lecture associés, chaque fois qu’une modification de ses données sous-jacentes se produit.

## <a name="transactional-support"></a>Prise en charge transactionnelle

Si les requêtes sur les microservices sont difficiles, l’implémentation d’une transaction entre les microservices peut être complexe. Le défi inhérent à la gestion de la cohérence des données entre les sources de données qui résident dans des microservices différents ne peut pas être sous-état. La figure 5-8 illustre le problème.

![Transaction dans le modèle saga](./media/saga-transaction-operation.png)

**Figure 5-8**. Implémentation d’une transaction sur des microservices

Notez comment, dans la figure précédente, cinq microservices indépendants participent à une transaction de *commande de création* distribuée. Toutefois, la transaction pour chacun des cinq microservices individuels doit être réussie, ou tous doivent abandonner et annuler l’opération. Alors que la prise en charge transactionnelle intégrée est disponible dans chacun des microservices, il n’existe pas de prise en charge d’une transaction distribuée sur les cinq services.

Étant donné que la prise en charge transactionnelle est essentielle pour que cette opération maintienne les données cohérentes dans chacun des microservices, vous devez construire par programmation une transaction distribuée.

Un modèle répandu pour l’ajout par programmation de la prise en charge transactionnelle est le [modèle saga](https://blog.couchbase.com/saga-pattern-implement-business-transactions-using-microservices-part/). Elle est implémentée par le regroupement des transactions locales et l’appel séquentiel de chacune d’elles. En cas d’échec d’une transaction locale, saga abandonne l’opération et appelle un ensemble de [transactions de compensation](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction) pour annuler les modifications apportées par les transactions locales précédentes. La figure 5-9 montre une transaction ayant échoué avec le modèle saga.

![Restauration dans le modèle saga](./media/saga-rollback-operation.png)

**Figure 5-9**. Restauration d'une transaction

Notez comment, dans la figure précédente, l’opération *GenerateContent* a échoué dans le microservice musical. Le saga appelle les transactions de compensation (en rouge) pour supprimer le contenu, annuler le paiement et annuler la commande, en retournant les données pour chaque microservice dans un état cohérent.

Les modèles Saga sont généralement des chorégraphiés sous la forme d’une série d’événements connexes ou orchestrés sous la forme d’un ensemble de commandes associées.

## <a name="cqrs-pattern"></a>Modèle CQRS

CQRS, ou [séparation des responsabilités en matière de commande et de requête](https://docs.microsoft.com/azure/architecture/patterns/cqrs), est un modèle architectural qui sépare les opérations qui lisent les données de celles qui écrivent des données. Ce modèle peut contribuer à optimiser les performances, l’évolutivité et la sécurité.

Dans les scénarios d’accès aux données normaux, vous implémentez un seul modèle (objet d’entité et de référentiel) qui effectuent à la *fois des* opérations de lecture et d’écriture de données.

Toutefois, un scénario d’accès aux données plus avancé peut tirer parti de modèles et de tables de données distincts pour les lectures et les écritures. Pour améliorer les performances, l’opération de lecture, connue sous le nom de *requête*, peut interroger une représentation fortement dénormalisée des données afin d’éviter des jointures de table répétitives coûteuses. Tandis que l’opération d' *écriture* , appelée *commande*, peut être mise à jour par rapport à une représentation entièrement normalisée des données. Vous devez ensuite implémenter un mécanisme pour maintenir la synchronisation des deux représentations. En général, chaque fois que la table d’écriture est modifiée, elle déclenche un événement qui réplique la modification des données dans la table de lecture.

La figure 5-10 illustre une implémentation du modèle CQRS.

![Implémentation CQRS](./media/cqrs-implementation.png)

**Figure 5-10**. Implémentation CQRS

Notez comment, dans la figure précédente, des modèles de commande et de requête distincts sont implémentés. En outre, chaque opération d’écriture de données est enregistrée dans le magasin d’écriture, puis propagée vers le magasin de lecture. Portez une attention particulière à la façon dont le processus de propagation opère sur le principe de [cohérence éventuelle](https://www.cloudcomputingpatterns.org/eventual_consistency/), tandis que le modèle de lecture finit par se synchroniser avec le modèle d’écriture, mais il peut y avoir un décalage dans le processus.

En implémentant la séparation, vous avez la possibilité de mettre à l’échelle les lectures et les écritures séparément. En outre, vous pouvez imposer une sécurité plus étroite sur les opérations d’écriture que celles relatives aux lectures.

En règle générale, les modèles CQRS sont appliqués à des sections limitées de votre système en fonction de vos besoins spécifiques.

## <a name="relational-vs-nosql"></a>Comparaison entre NoSQL et NoSQL

L’impact des technologies [NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) ne peut pas être surétat, en particulier pour les systèmes Cloud natifs distribués. La prolifération des nouvelles technologies de données dans cet espace a perturbé les solutions qui, une fois exclusivement, s’appuyaient sur des bases de données relationnelles.

D’un côté, les bases de données relationnelles ont été une technologie répandue depuis des décennies. Elles sont matures, éprouvées et largement implémentées. Les produits de base de données concurrents, l’expertise et les outils sont nombreux. Les bases de données relationnelles fournissent un magasin de tables de données associées. Ces tables ont un schéma fixe, utilisent SQL (langage SQL) pour gérer les données et ont des garanties [acid](https://www.geeksforgeeks.org/acid-properties-in-dbms/) (également appelées atomicité, cohérence, isolation et durabilité).

Les bases de données non-SQL, de l’autre côté, font référence à des magasins de données non relationnels, à hautes performances. Ils utilisent Excel dans leurs caractéristiques de facilité d’utilisation, d’évolutivité, de résilience et de disponibilité. Au lieu de joindre des tables de données normalisées, NoSQL stocke des données auto-descriptives (sans schéma) généralement dans des documents JSON. Ils n’offrent pas de garanties [acid](https://www.geeksforgeeks.org/acid-properties-in-dbms/) .

Un moyen de comprendre les différences entre ces types de bases de données se trouve dans le registre des [Cap](https://towardsdatascience.com/cap-theorem-and-distributed-database-management-systems-5c2be977950e), un ensemble de principes qui peuvent être appliqués aux systèmes distribués qui stockent l’État. La figure 5-11 montre les trois propriétés de l’embout de CAP.

![CAP CAP](./media/cap-theorem.png)

**Figure 5-11**. Le niveau de CAP

Le titre de l’état d’un système de données distribuées offre un compromis entre cohérence, disponibilité et tolérance de partition, et n’importe quelle base de données ne peut garantir que deux des trois propriétés :

- *Cohérence*: chaque nœud du cluster répondra avec les données les plus récentes, même s’il nécessite de bloquer une demande jusqu’à ce que tous les réplicas soient correctement mis à jour.

- *Disponibilité*: chaque nœud renvoie une réponse dans un laps de temps raisonnable, même si cette réponse n’est pas les données les plus récentes.

- *Tolérance*de la partition : garantit que le système continuera à fonctionner en cas de défaillance d’un nœud ou de perte de la connectivité avec un autre.

Les bases de données relationnelles présentent la cohérence et la disponibilité, mais pas la tolérance de partition. Le partitionnement d’une base de données relationnelle, telle que partitionnement, est difficile et peut avoir un impact sur les performances.

En revanche, les bases de données NoSQL présentent généralement la tolérance de la partition, appelée évolutivité horizontale et haute disponibilité. À mesure que le niveau de CAP spécifie, vous ne pouvez avoir que deux des trois principes et vous perdez la propriété Consistency.

Les bases de données NoSQL sont distribuées et généralement mises à l’échelle sur les serveurs de base. Cela peut offrir une disponibilité exceptionnelle, à la fois dans et dans les régions géographiques à un coût réduit. Les données peuvent être partitionnées et répliquées sur ces ordinateurs, ou nœuds, fournissant ainsi une redondance et une tolérance de panne. L’inconvénient est la cohérence. Une modification des données sur un nœud NoSQL peut prendre un certain temps pour se propager à d’autres nœuds. En règle générale, un nœud de base de données NoSQL fournit une réponse immédiate à une requête, même si les données qu’elle présente sont obsolètes et n’ont pas encore été mises à jour.

Il s’agit d’une [cohérence éventuelle](https://www.cloudcomputingpatterns.org/eventual_consistency/), caractéristique des systèmes de données distribués où les transactions ACID ne sont pas prises en charge. Il s’agit d’un bref délai entre la mise à jour d’un élément de données et le temps nécessaire à la propagation de cette mise à jour à chacun des nœuds de réplica. Si vous mettez à jour un élément de produit dans une base de données NoSQL dans le États-Unis, mais en même temps interrogez ce même élément de données à partir d’un nœud de réplica en Europe, vous pouvez récupérer les informations de produit antérieures, jusqu’à ce que le nœud européen ait été mis à jour avec la modification du produit. Le compromis est qu’en donnant une [cohérence forte](https://en.wikipedia.org/wiki/Strong_consistency), en attendant que tous les nœuds de réplica soient mis à jour avant de retourner un résultat de requête, vous pouvez prendre en charge une grande échelle et un volume de trafic énorme, mais avec la possibilité de présenter des données plus anciennes.

Les bases de données NoSQL peuvent être classées selon les quatre modèles suivants :

- *Magasin de documents* (MongoDB, CouchDB, Couchbase) : les données (et les métadonnées correspondantes) sont stockées de façon non relationnelle dans des documents JSON dénormalisés à l’intérieur de la base de données.

- *Stockage de clé/valeur* (redims, Riak, Memcached) : les données sont stockées dans des paires clé-valeur simples avec des opérations système effectuées par rapport à une clé d’accès unique qui est mappée à une valeur de données utilisateur.

- *Stockage à colonnes larges* (HBase, Cassandra) : les données associées sont stockées dans un format de colonne sous la forme d’un ensemble de paires clé/valeur imbriquées au sein d’une même colonne avec des données généralement récupérées en tant qu’unité unique sans devoir joindre plusieurs tables.

- *Magasins de graphiques* (neo4j, Titan) : les données sont stockées sous la forme d’une représentation graphique au sein d’un nœud avec les bords qui spécifient la relation entre les nœuds.

Les bases de données NoSQL peuvent être optimisées pour gérer les données à grande échelle, en particulier lorsque les données sont relativement simples. Prenons l’exemple d’une base de données NoSQL :

- Votre charge de travail nécessite une grande échelle et une haute concurrence.
- Vous avez un grand nombre d’utilisateurs.
- Vos données peuvent être exprimées simplement sans relations.
- Vous devez distribuer vos données géographiquement.
- Vous n’avez pas besoin de garanties ACID.
- Sera déployé sur le matériel de produit.

Envisagez ensuite une base de données relationnelle lorsque :

- Vos charges de travail nécessitent une échelle moyenne à grande.
- La concurrence n’est pas un problème majeur.
- Des garanties ACID sont nécessaires.
- Les données sont mieux exprimées de manière relationnelle.
- Votre application sera déployée sur un matériel haut de gamme.

Ensuite, nous examinons le stockage des données dans le Cloud Azure.

>[!div class="step-by-step"]
>[Précédent](distributed-data.md)
>[Suivant](azure-data-storage.md)
