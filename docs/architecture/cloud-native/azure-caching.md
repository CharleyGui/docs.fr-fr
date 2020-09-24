---
title: Mise en cache dans une application cloud native
description: En savoir plus sur les stratégies de mise en cache dans une application Cloud native.
author: robvet
ms.date: 05/17/2020
ms.openlocfilehash: 84860ad4583e4b45d5ca9490d9f0167e7439d3d4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161085"
---
# <a name="caching-in-a-cloud-native-app"></a>Mise en cache dans une application Cloud Native

Les avantages de la mise en cache sont bien compris. La technique consiste à copier temporairement les données fréquemment sollicitées à partir d’un magasin de données principal vers un *stockage rapide* situé plus près de l’application. La mise en cache est souvent implémentée où...

- Les données restent relativement statiques.
- L’accès aux données est lent, en particulier par rapport à la vitesse du cache.
- Les données sont soumises à des niveaux élevés de contention.

## <a name="why"></a>Pourquoi ?

Comme indiqué dans le [Guide de mise en cache de Microsoft](/azure/architecture/best-practices/caching), la mise en cache peut améliorer les performances, l’extensibilité et la disponibilité des microservices individuels et du système dans son ensemble. Elle réduit la latence et la contention de la gestion de grands volumes de demandes simultanées à un magasin de données. À mesure que le volume de données et le nombre d’utilisateurs augmentent, plus les avantages de la mise en cache sont importants.

La mise en cache est plus efficace quand un client lit à plusieurs reprises des données immuables ou rarement modifiées. Il peut s’agir d’informations de référence, telles que des informations sur les produits et les tarifs, ou de ressources statiques partagées qui sont coûteuses à construire.

Si les microservices doivent être sans État, un cache distribué peut prendre en charge l’accès simultané aux données d’état de session quand cela est absolument requis.

Envisagez également la mise en cache pour éviter les calculs répétitifs. Si une opération transforme des données ou effectue un calcul complexe, met en cache le résultat pour les demandes suivantes.

## <a name="caching-architecture"></a>Architecture de la mise en cache

Les applications Cloud natives implémentent généralement une architecture de mise en cache distribuée. Le cache est hébergé en tant que service de [sauvegarde](./definition.md#backing-services)Cloud, distinct des microservices. La figure 5-15 illustre l’architecture.

![Mise en cache dans une application Cloud Native](media/caching-in-a-cloud-native-app.png)

**Figure 5-15**: mise en cache dans une application Cloud Native

Dans l’illustration précédente, Notez que le cache est indépendant et partagé par les microservices. Dans ce scénario, le cache est appelé par la [passerelle d’API](./front-end-communication.md). Comme indiqué dans le chapitre 4, la passerelle sert de serveur frontal pour toutes les demandes entrantes. Le cache distribué augmente la réactivité du système en retournant les données mises en cache dans la mesure du possible. En outre, la séparation du cache des services permet au cache d’être mis à l’échelle indépendamment pour répondre aux demandes de trafic accrues.

La figure précédente présente un modèle de mise en cache courant connu sous le nom de [modèle de cache](/azure/architecture/patterns/cache-aside). Pour une demande entrante, vous devez d’abord interroger le cache (étape \# 1) pour obtenir une réponse. Si elle est trouvée, les données sont retournées immédiatement. Si les données n’existent pas dans le cache (ce qui s’appelle une absence dans le [cache](https://www.techopedia.com/definition/6308/cache-miss)), elles sont récupérées à partir d’une base de données locale dans un service en aval (étape \# 2). Elle est ensuite écrite dans le cache pour les demandes ultérieures (étape \# 3) et retournée à l’appelant. Vous devez veiller à supprimer régulièrement les données mises en cache afin que le système reste en temps et en cohérence.

À mesure qu’un cache partagé augmente, il peut s’avérer bénéfique de partitionner ses données sur plusieurs nœuds. Cela permet de réduire la contention et d’améliorer l’évolutivité. De nombreux services de mise en cache prennent en charge la possibilité d’ajouter et de supprimer dynamiquement des nœuds et de rééquilibrer les données entre les partitions. Cette approche implique généralement le clustering. Le clustering expose une collection de nœuds fédérés sous la forme d’un cache unique et transparent. En interne, toutefois, les données sont dispersées sur les nœuds à la suite d’une stratégie de distribution prédéfinie qui équilibre la charge uniformément.

## <a name="azure-cache-for-redis"></a>Cache Azure pour Redis

Le [cache Azure pour redims](https://azure.microsoft.com/services/cache/) est un service de mise en cache des données sécurisé et de service Broker de messagerie, entièrement géré par Microsoft. Utilisé comme offre PaaS (Platform as a service), il fournit un débit élevé et un accès à faible latence aux données. Le service est accessible à toutes les applications situées à l’intérieur ou à l’extérieur d’Azure.

Le service cache Azure pour Redims gère l’accès aux serveurs ReDim Open source hébergés dans des centres de données Azure. Le service agit comme une façade assurant la gestion, le contrôle d’accès et la sécurité. Le service prend en charge en mode natif un ensemble complet de structures de données, notamment des chaînes, des hachages, des listes et des ensembles. Si votre application utilise déjà des ReDim, elle fonctionnera comme avec le cache Azure pour les opérations ReDim.

Le cache Azure pour les insertions est plus qu’un simple serveur de cache. Il peut prendre en charge un certain nombre de scénarios pour améliorer une architecture de microservices :

- Un magasin de données en mémoire
- Une base de données non relationnelle distribuée
- Un courtier de messages
- Un serveur de configuration ou de découverte
  
Pour les scénarios avancés, une copie des données mises en cache peut être [conservée sur le disque](/azure/azure-cache-for-redis/cache-how-to-premium-persistence). Si un événement catastrophique désactive à la fois les caches principal et réplica, le cache est reconstruit à partir de l’instantané le plus récent.

Le cache Redims Azure est disponible dans un certain nombre de configurations prédéfinies et de niveaux tarifaires. Le [niveau Premium](/azure/azure-cache-for-redis/cache-overview#service-tiers) offre de nombreuses fonctionnalités de niveau entreprise, telles que le clustering, la persistance des données, la géo-réplication et l’isolation du réseau virtuel.

>[!div class="step-by-step"]
>[Précédent](relational-vs-nosql-data.md) 
> [Suivant](elastic-search-in-azure.md)
