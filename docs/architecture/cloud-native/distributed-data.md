---
title: Données distribuées
description: Architecture des applications .NET natives Cloud pour Azure | Données distribuées pour les applications Cloud natives
ms.date: 06/30/2019
ms.openlocfilehash: b715ae5203264a023bc9f911aa74ee222afe3d68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087447"
---
# <a name="distributed-data-for-cloud-native-apps"></a>Données distribuées pour les applications Cloud natives

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Lors de la construction d’un système Cloud natif qui se compose de nombreux microservices indépendants, la façon dont vous pensez aux modifications du stockage de données.

Les applications monolithiques traditionnelles favorisent une banque de données centralisée illustrée dans la figure 5-1.

![Base de données monolithique unique](./media/single-monolithic-database.png)

**Figure 5-1**. Base de données monolithique unique

Notez dans la figure précédente comment tous les composants d’application consomment une base de données relationnelle unique.

Cette approche présente de nombreux avantages. Il est facile d’interroger les données réparties sur plusieurs tables et il est facile d’implémenter des [transactions ACID](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) qui garantissent la cohérence des données. Vous obtenez toujours une *cohérence immédiate*: toutes vos mises à jour de données ou aucune d’elles ne le fait.

Les systèmes natifs du Cloud favorisent une architecture de données illustrée dans la figure 5-2, dans laquelle chaque microservice possède et encapsule ses propres données.

![Plusieurs bases de données entre les microservices](./media/data-across-microservices.png)

**Figure 5-2**. Plusieurs bases de données entre les microservices

Notez comment, dans la figure précédente, chaque microservice possède et encapsule le magasin de données informatique et expose uniquement des données au monde extérieur à partir de son API publique.

Ce modèle permet à chaque microservice d’évoluer indépendamment sans avoir à coordonner les modifications du schéma de données avec d’autres microservices. Chaque microservice est libre d’implémenter le type de magasin de données (base de données relationnelle, base de données de documents, magasin clé-valeur) qui correspond le mieux à ses besoins. Lors de l’exécution, chaque microservice peut mettre à l’échelle ses données en conséquence. Cela est illustré dans la figure 5-3 :

![Persistance des données polyglotte](./media/polyglot-data-persistence.png)

**Figure 5-3**. Persistance des données polyglotte

Notez comment, dans la figure précédente, le catalogue de produits et les microservices d’inventaire adoptent les bases de données relationnelles, le microservice de commande, une base de données de documents NoSql et le microservice de panier d’achat, qui est un magasin de valeurs de clé externe. Bien que les bases de données relationnelles restent pertinentes pour les microservices avec des données complexes, les bases de données NoSQL ont acquis une popularité considérable, offrant ainsi une adaptation, une recherche rapide et une haute disponibilité. Leur nature sans schéma permet aux développeurs de quitter une architecture de classes de données typées et de ORM, ce qui rend la modification coûteuse et fastidieuse.

>[!div class="step-by-step"]
>[Précédent](service-mesh-communication-infrastructure.md)
>[Suivant](data-patterns.md)
