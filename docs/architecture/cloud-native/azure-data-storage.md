---
title: Stockage de données dans Azure
description: Architecture des applications .NET natives Cloud pour Azure | Stockage de données dans Azure
ms.date: 06/30/2019
ms.openlocfilehash: 1a86cecf005c6dbdfda5cf4cacfafaad4711c076
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087766"
---
# <a name="data-storage-in-azure"></a>Stockage de données dans Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Comme nous l’avons vu dans ce livre, le Cloud change la façon dont les applications sont conçues, déployées et gérées. Lors de la migration vers le Cloud, il est important de savoir comment déplacer vos données ? Heureusement, le Cloud Azure offre de nombreuses options.

Vous pouvez simplement approvisionner une machine virtuelle Azure et installer votre base de données de votre choix. C’est ce que l’on appelle [infrastructure en tant que service (IaaS)](https://www.techopedia.com/definition/141/infrastructure-as-a-service-iaas). Cette approche simplifie le déplacement d’une base de données locale vers le Cloud, en l’évolution, tout en décalant la charge de la gestion de la machine virtuelle et de la base de données.

Au lieu de cela, une [base de données en tant que service (DBaaS)](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/) entièrement managée est une meilleure option. Vous bénéficiez de nombreuses fonctionnalités intégrées lorsque l’hébergement, la maintenance et la gestion des licences sont gérés par Microsoft. Azure propose différents types d’options de stockage de données entièrement gérées, chacune avec des avantages spécifiques. Ils prennent tous en charge la capacité juste-à-temps et un modèle de paiement à l’accès.

Nous allons ensuite examiner les options DBaaS disponibles dans Azure. Vous verrez comment Microsoft continue s’engage à maintenir Azure une « plateforme ouverte », offrant une prise en charge gérée pour de nombreuses bases de données relationnelles et NoSQL Open source et effectuant des contributions clés aux différents fondations Open source en tant que membre actif.

## <a name="azure-sql-database"></a>Base de données SQL Azure

[Azure SQL Database](https://docs.microsoft.com/azure/sql-database/) est une base de données relationnelle en tant que service (DBaaS) riche en fonctionnalités, basée sur les moteur de base de données Microsoft SQL Server. Elle est entièrement gérée par Microsoft et est une base de données Cloud haute performance, fiable et sécurisée. Le service partage un grand nombre des fonctionnalités présentes dans la version locale de SQL Server.

Vous pouvez approvisionner un serveur et une base de données SQL Database en quelques minutes. Lorsque la demande de votre application passe de quelques clients à des millions, Azure SQL Database évolue à la volée avec un temps d’arrêt minimal. Vous pouvez ajouter ou supprimer dynamiquement des ressources, notamment la puissance de l’UC, la mémoire, le débit d’e/s et le stockage alloué à vos bases de données.

La figure 5-12 montre les options de déploiement pour Azure SQL Database.

![Options de déploiement Azure SQL](./media/azure-sql-database-deployment-options.png)

**Figure 5-12**. Options de déploiement Azure SQL

Notez les alternatives de la figure précédente lors du déploiement d’une SQL Database :

- Une [seule base de données](https://docs.microsoft.com/azure/sql-database/sql-database-single-database) avec son propre ensemble de ressources gérées par un [serveur SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-servers). Une base de données unique est similaire à une [base de données à relation contenant-contenu](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) dans un déploiement SQL Server local.

- [Pool élastique](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-pool) dans lequel une collection de bases de données SQL partage un seul serveur de SQL Database à un prix défini. Les bases de données uniques peuvent être déplacées vers et à l’extérieur d’un pool élastique en fonction des besoins afin d’optimiser les performances du prix d’un groupe de bases de données.

- Une [Managed instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) dans laquelle est une collection de bases de données système et utilisateur offre une compatibilité à presque 100% avec un SQL Server local. Cette option prend en charge les bases de données plus volumineuses, jusqu’à 35 to, et est placée dans un [réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) pour une meilleure isolation.

Azure SQL Database est une [moteur de base de données PaaS (Platform as a service)](https://docs.microsoft.com/azure/sql-database/sql-database-paas) entièrement gérée qui gère la mise à niveau, les mises à jour correctives, les sauvegardes et la surveillance sans intervention de l’utilisateur. Il exécute toujours la dernière version stable de la SQL Server Moteur de base de données et du système d’exploitation corrigé, et garantit une disponibilité de 99,99%. Une fonctionnalité, [géo-réplication Active](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication), vous permet de créer des bases de données secondaires accessibles en lecture dans le même ou dans un autre centre de données Azure. En cas d’échec, un basculement vers une base de données secondaire peut être initié. À ce stade, les autres secondaires sont automatiquement liés à la nouvelle base de données primaire. Jusqu’à quatre réplicas secondaires sont pris en charge dans la même région ou dans des régions différentes, et ces secondaires peuvent également être utilisés pour les requêtes d’accès en lecture seule.

Azure SQL Database intègre des fonctionnalités [intégrées de surveillance et de réglage intelligent](https://docs.microsoft.com/azure/sql-database/sql-database-monitoring-tuning-index) qui peuvent vous aider à optimiser les performances et à réduire les coûts d’exploitation. Par exemple, la fonctionnalité de [réglage automatique](https://docs.microsoft.com/azure/sql-database/sql-database-automatic-tuning) fournit un réglage continu des performances basé sur l’intelligence artificielle et machine learning. Le service apprend à vos charges de travail en cours d’exécution et peut appliquer des recommandations de paramétrage. Plus un Azure SQL Database s’exécute avec un réglage automatique activé, plus il fonctionne.

[Azure SQL Database sans serveur](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) (disponible en version préliminaire lors de la rédaction de ce livre) est un niveau de calcul pour les bases de données uniques qui évolue automatiquement en fonction de la demande de la charge de travail et des factures pour la quantité de calcul utilisée par seconde. Le niveau de calcul sans serveur suspend également automatiquement les bases de données pendant les périodes inactives afin que seuls les frais de stockage soient facturés. Il reprend automatiquement lorsque l’activité est retournée.

Enfin, il existe la nouvelle [Azure SQL Database niveau tarifaire hyperscale](https://azure.microsoft.com/services/sql-database/) . Elle est optimisée par une architecture de stockage hautement évolutive et permet à votre base de données de croître en fonction des besoins, ce qui évite d’avoir à préconfigurer les ressources de stockage. Vous pouvez mettre à l’échelle des ressources de calcul et de stockage indépendamment, ce qui offre la flexibilité nécessaire pour optimiser les performances de chaque charge de travail. Azure SQL Database hyperscale est optimisé pour le traitement [OLTP](https://en.wikipedia.org/wiki/Online_transaction_processing) et les charges de travail analytiques à débit élevé avec un stockage allant jusqu’à 100 to.  Avec les charges de travail nécessitant beaucoup de ressources de lecture, hyperscale fournit une montée en charge rapide en approvisionnant des réplicas de lecture supplémentaires en fonction des besoins pour le déchargement des charges de travail de lecture.

Outre la pile de Microsoft SQL Server traditionnelle, Azure propose également des versions gérées de plusieurs bases de données Open source populaires.

## <a name="azure-database-for-mysql"></a>Azure Database pour MySQL

[MySQL](https://en.wikipedia.org/wiki/MySQL)  est une  [base de données relationnelle](https://en.wikipedia.org/wiki/Open-source_software)  [Open source](https://en.wikipedia.org/wiki/Relational_database_management_system). Il s’agit d’un composant de la [pile de logiciels LAMP](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) et utilisé par de nombreuses grandes organisations, notamment Facebook, Twitter et YouTube. L’édition Community est disponible gratuitement et l’édition Enterprise requiert un achat de licence. Initialement créé dans 1995, le produit a été acheté par Sun Microsystems dans 2008, qui a été acquis par Oracle au 2010.

[Azure Database pour MySQL](https://azure.microsoft.com/services/mysql/) est un service de base de données relationnelle entièrement géré, adapté à l’entreprise et basé sur le moteur Open source MySQL Server. En implémentant MySQL Community Edition, il comprend les fonctionnalités PaaS suivantes sans coût supplémentaire :

- [Haute disponibilité](https://docs.microsoft.com/azure/mysql/concepts-high-availability)intégrée.

- Des performances prévisibles, à l’aide de la tarification inclusive de [paiement à l'](https://docs.microsoft.com/azure/mysql/concepts-pricing-tiers)utilisation.

- Mise à l' [échelle](https://docs.microsoft.com/azure/mysql/concepts-high-availability) en quelques secondes.

- Sécurisé pour protéger les données sensibles au repos et en mouvement.

- [Sauvegardes automatiques](https://docs.microsoft.com/azure/mysql/concepts-backup) et [restauration](https://docs.microsoft.com/azure/mysql/concepts-backup) jusqu’à une date et heure jusqu’à 35 jours.

- Sécurité et conformité à l’échelle de l’entreprise.

Ces fonctionnalités PaaS intégrées sont importantes pour les organisations qui ont des centaines de bases de données « tactiques » (non stratégiques) dans leurs centres de données, mais qui n’ont pas les ressources nécessaires pour effectuer les mises à jour correctives, la sauvegarde, la sécurité et la surveillance des performances.

En outre, [Azure Data Migration Service](https://azure.microsoft.com/services/database-migration/) peut migrer des données de plusieurs sources de base de données vers des plateformes de données Azure avec un temps d’arrêt minimal. Le service génère des rapports d’évaluation et fournit des recommandations pour vous guider à travers les modifications requises pour effectuer une migration, à la fois petite ou grande.

Le [serveur Azure MySQL](https://docs.microsoft.com/azure/mysql/concepts-servers) géré est le point d’administration central pour le service. Il s’agit du même moteur MySQL Server utilisé pour les déploiements sur site. Avec elle, vous pouvez créer une seule base de données par serveur pour utiliser toutes les ressources ou créer plusieurs bases de données par serveur pour partager des ressources. Votre équipe peut continuer à développer des applications avec les outils open source et la plateforme de votre choix sans avoir à acquérir de nouvelles compétences ni à gérer des machines virtuelles et une infrastructure.

## <a name="azure-database-for-mariadb"></a>Azure Database for MariaDB

[MariaDB](https://mariadb.com/) Le serveur est un autre serveur de base de données Open source populaire. Il a été créé en tant que fourche de MySQL par les développeurs d’origine de MySQL au moment où Oracle a acheté Sun Microsystems qui possédait MySQL. L’objectif était de s’assurer que MariaDB restait Open source.

Étant donné que MariaDB est une [fourche de MySQL](https://blog.panoply.io/a-comparative-vmariadb-vs-mysql), les définitions de données et de table sont compatibles, et les protocoles, structures et API du client sont à la fois étroits. Les connecteurs de données MySQL fonctionnent MariaDB sans modification.

MariaDB a une bonne suite et est utilisée par de nombreuses grandes entreprises. Bien qu’Oracle continue à gérer, améliorer et prendre en charge MySQL, MariaDB est géré par MariaDB Foundation qui autorise les contributions publiques au produit et à la documentation.

[Azure Database for MariaDB](https://azure.microsoft.com/services/mariadb/) est une base de données entièrement gérée en tant que service dans le Cloud Azure. Il est basé sur le moteur du serveur [MariaDB Community Edition](https://mariadb.org/download/) . Il peut gérer les charges de travail critiques avec des performances prévisibles et une évolutivité dynamique. À l’instar des autres plateformes de base de données Azure, il comprend de nombreuses fonctionnalités de plateforme en tant que service sans coût supplémentaire :

- [Haute disponibilité](https://docs.microsoft.com/azure/mariadb/concepts-high-availability)intégrée.

- Des performances prévisibles, à l’aide de la tarification inclusive de [paiement à l'](https://docs.microsoft.com/azure/mariadb/concepts-pricing-tiers)utilisation.

- [Mise à l’échelle](https://docs.microsoft.com/azure/mariadb/concepts-high-availability) en quelques secondes.

- Protection sécurisée des données sensibles au repos et en mouvement.

- [Sauvegardes automatiques](https://docs.microsoft.com/azure/mariadb/concepts-backup) et [restauration](https://docs.microsoft.com/azure/mariadb/concepts-backup) jusqu’à une date et heure jusqu’à 35 jours.

- Sécurité et conformité à l’échelle de l’entreprise.

## <a name="azure-database-for-postgresql"></a>Azure Database pour PostgreSQL

[PostgreSQL](https://www.postgresql.org/) est une autre base de données relationnelle Open source populaire avec plus de 30 ans de développement actif. Il s’agit d’un système de gestion de base de données à usage général et relationnel objet. Ses licences sont considérées comme « libérales » et le produit est libre d’utiliser, de modifier et de distribuer dans n’importe quel format. De nombreuses grandes entreprises, dont Apple, Red Hat et Fujitsu, ont créé des produits à l’aide de PostgreSQL.

[Azure Database pour PostgreSQL](https://azure.microsoft.com/services/postgresql/) est un service de base de données relationnelle entièrement géré, basé sur le moteur de base de données postgres Open source. Il peut gérer des charges de travail stratégiques avec des performances prévisibles, une sécurité, une haute disponibilité et une évolutivité dynamique. Il prend en charge plusieurs langages et infrastructures Open source, C++notamment, Java, Python, Node, C\#et php. Il permet la [migration](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) de bases de données PostgreSQL via une interface de ligne de commande ou le [service de migration de données Azure](https://azure.microsoft.com/services/database-migration/).

Le service inclut [une intelligence intégrée](https://docs.microsoft.com/azure/postgresql/concepts-monitoring) qui étudie vos modèles de base de données uniques et fournit des recommandations et des informations personnalisées pour vous aider à optimiser les performances de votre base de données PostgreSQL. [Advanced Threat Protection](https://docs.microsoft.com/azure/postgresql/concepts-data-access-and-security-threat-protection) surveille votre base de données autour de l’horloge et détecte les activités malveillantes potentielles, en vous avertissant de la détection pour vous permettre d’intervenir immédiatement.

La base de données Azure pour PostgreSQL est disponible sous la forme de deux options de déploiement : serveur unique et hyperscale (CITUS), disponible en version préliminaire lors de la rédaction de ce livre

- L’option de déploiement de [serveur unique](https://docs.microsoft.com/azure/postgresql/concepts-servers) est un point d’administration central pour plusieurs bases de données. Il s’agit du même moteur de serveur PostgreSQL que celui disponible pour les déploiements locaux. Avec elle, vous pouvez créer une seule base de données par serveur pour utiliser toutes les ressources ou créer plusieurs bases de données pour partager les ressources. La tarification est structurée par serveur en fonction des cœurs et du stockage.

- L' [option hyperscale (CITUS)](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) est optimisée par la technologie de de [données CITUS](https://www.citusdata.com/) . Il permet une mise à l’échelle hautes performances grâce à la mise à l’échelle horizontale d’une base de données sur des centaines de nœuds afin de fournir des performances et une évolutivité très rapides. Cette option permet au moteur d’intégrer plus de données en mémoire, de paralléliser les requêtes sur des centaines de nœuds et d’indexer les données plus rapidement. La fonctionnalité hyperscale est compatible avec les dernières innovations, versions et outils pour PostgreSQL, ce qui vous permet de tirer parti de votre expertise PostgreSQL existante.

## <a name="cosmos-db"></a>Cosmos DB

Azure Cosmos DB est un service de base de données NoSQL entièrement géré et distribué à l’échelle mondiale, conçu pour offrir une faible latence, une évolutivité élastique, une cohérence des données gérées et une haute disponibilité. En bref, si votre application a besoin d’un temps de réponse rapide partout dans le monde, s’il doit être toujours en ligne et nécessite une évolutivité illimitée et élastique du débit et du stockage, Cosmos DB est un bon choix. La figure 5-13 montre une vue d’ensemble de haut niveau de Cosmos DB.

![Vue d’ensemble de Cosmos DB](./media/cosmos-db-overview.png)

**Figure 5-13**: vue d’ensemble des Cosmos DB

Notez dans la figure 5-13 Comment Cosmos DB est un service de base de données robuste et hautement polyvalent avec de nombreuses fonctionnalités Cloud natives intégrées. Dans cette section, nous examinerons les détails.

### <a name="global-support"></a>Support global

Vous pouvez distribuer globalement des bases de données Cosmos dans toutes les régions Azure dans le monde entier, en plaçant les données à proximité de vos utilisateurs, en améliorant le temps de réponse et en réduisant la latence. Vous pouvez ajouter ou supprimer une base de données d’une région sans interrompre ou redéployer votre application. En arrière-plan, Cosmos DB réplique en toute transparence les données dans toutes les régions configurées.

Cosmos DB prend en charge le clustering [actif/actif](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) au niveau global, ce qui vous permet de configurer toutes les régions de votre base de données pour prendre en charge les écritures et les lectures.

La fonctionnalité de protocole [multimaître](https://docs.microsoft.com/azure/cosmos-db/how-to-multi-master) dans Cosmos DB active les fonctionnalités suivantes :

- Écriture élastique illimitée et évolutivité de lecture.

- 99,999% de la disponibilité en lecture et en écriture partout dans le monde.

- Lectures et écritures garanties traitées en moins de 10 millisecondes au 99e centile.

En interne, Cosmos DB gère la réplication des données entre régions avec des garanties de niveau de cohérence et des contrats de niveau de service soutenu financièrement.

Avec l’Cosmos DB les [API d’hébergement multiple](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), votre application peut automatiquement prendre connaissance de la région Azure la plus proche et lui envoyer des requêtes. La région la plus proche est identifiée par Cosmos DB sans aucune modification de configuration. Si une région n’est plus disponible, Cosmos DB prend en charge le basculement automatique, et la fonctionnalité d’hébergement multiple achemine automatiquement votre demande vers la région disponible la plus proche.

### <a name="multi-model-support"></a>Prise en charge de plusieurs modèles

Cosmos DB est une *plateforme de données à plusieurs modèles* qui vous permet d’interagir avec vos données à l’aide d’un certain nombre de modèles NoSQL pris en charge, notamment des documents, des paires clé-valeur, des colonnes larges et des représentations graphiques. En interne, les données sont stockées dans un format de [struct](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/using-structs) simple constitué de types de données primitifs, notamment des chaînes, des valeurs booléennes et des nombres. Pour chaque demande, le moteur de base de données traduit les données dans la représentation du modèle que vous avez sélectionnée. Vous avez le choix entre une API propriétaire Cosmos DB SQL ou l’une des [API de compatibilité](https://www.wikiwand.com/en/Cosmos_DB) illustrée dans la figure 5-14.

![Fournisseurs de Cosmos DB](./media/cosmos-db-providers.png)

**Figure 5-14**: fournisseurs Cosmos DB

Notez dans la figure 5-14 Comment Cosmos DB prend en charge le [stockage table](https://azure.microsoft.com/services/storage/tables/). Les Cosmos DB et le [stockage table Azure](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) partagent le même modèle de table sous-jacent et exposent nombre des mêmes opérations de table. Toutefois, le [Cosmos DB API table](https://docs.microsoft.com/azure/cosmos-db/table-introduction) fournit de nombreuses améliorations de haut niveau non disponibles dans l’API Azure Storage. Ces fonctionnalités sont comparées à la figure 5-15.

![API Table Azure](./media/azure-table-api.png)

**Figure 5-15**: API table Azure

Les applications écrites pour le stockage de tables Azure peuvent migrer vers Azure Cosmos DB à l’aide de la API Table sans aucune modification de code.

Dans les scénarios d’application [Brownfield](https://en.wikipedia.org/wiki/Brownfield_(software_development)) , les équipes de développement peuvent migrer des bases de données Mongo, Gremlin ou Cassandra existantes vers Cosmos DB avec des modifications minimes du code de données ou d’application existant. Pour les scénarios [Greenfield](https://en.wikipedia.org/wiki/Greenfield_project) , les équipes de développement peuvent choisir le modèle de données qui répond le mieux à leurs exigences et préférences, y compris les options Open source entièrement prises en charge pour les plateformes MongoDB, Cassandra et Gremlin.

### <a name="consistency-models"></a>Modèles de cohérence

Plus haut dans la section *relationnel et NoSQL* , nous avons abordé l’objet de la *cohérence des données*, qui est un terme qui fait référence à l’intégrité de vos données. Les bases de données distribuées qui reposent sur la réplication pour une haute disponibilité, une faible latence, ou les deux, doivent faire un compromis fondamental entre cohérence des lectures, disponibilité et latence.

La plupart des bases de données distribuées permettent aux développeurs de choisir entre deux modèles de cohérence : une [cohérence forte](https://en.wikipedia.org/wiki/Strong_consistency) et une [cohérence éventuelle](https://en.wikipedia.org/wiki/Eventual_consistency). Une *cohérence forte* est la norme Gold de la programmabilité des données. Elle garantit qu’un résultat de requête renverra toujours les données les plus récentes, même si le système doit subir une latence en attendant qu’une mise à jour soit répliquée sur toutes les copies de base de données. En revanche, un système configuré pour la *cohérence éventuelle* renverra des données immédiatement, même si ces données ne sont pas la copie la plus récente. Cette option permet une disponibilité plus élevée, une mise à l’échelle supérieure et des performances accrues.

Azure Cosmos DB offre un large éventail de [cinq modèles de cohérence bien définis](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) illustrés dans la figure 5-16. Ces options vous permettent d’effectuer des choix précis et des compromis précis en ce qui concerne la disponibilité et les performances en fonction des besoins de votre application. Ces modèles sont bien définis, intuitifs et sauvegardés par les contrats de niveau de service (SLA).

![Cosmos DB niveaux de cohérence](./media/cosmos-db-consistency-levels.png)

**Figure 5-16**: Cosmos DB niveaux de cohérence

### <a name="partitioning"></a>Partitionnement

Azure Cosmos DB utilise le [partitionnement](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) automatique pour mettre à l’échelle la base de données afin de répondre aux besoins de performances de votre application.

Vous gérez les données de Cosmos DB données en créant des [bases de données, des conteneurs et des éléments](https://docs.microsoft.com/azure/cosmos-db/databases-containers-items), comme illustré dans la figure 5-17.

![Entités Cosmos DB](./media/cosmos-db-entities.png)

**Figure 5-17**: hiérarchie des entités Cosmos DB

Notez dans la figure 5-17 comment vous commencez par créer une base de données Cosmos DB à l’intérieur d’un compte de base de données. Cette base de données devient l’unité de gestion pour un ensemble de conteneurs. Un conteneur est un regroupement indépendant du schéma des éléments qui peut être exprimé sous la forme d’une collection, d’une table ou d’un graphique, en fonction de votre fournisseur d’API sélectionné (abordé dans la section précédente). Les éléments sont les données que vous ajoutez au conteneur et sont représentés sous forme de documents, de lignes, de nœuds ou d’arêtes. Par défaut, tous les éléments que vous ajoutez à un conteneur sont automatiquement indexés sans nécessiter d’index ou de gestion de schéma explicites.

Pour partitionner le conteneur, les éléments sont divisés en sous-ensembles distincts appelés [partitions logiques](https://docs.microsoft.com/azure/cosmos-db/partition-data). Les partitions logiques sont créées en fonction de la valeur d’une clé de partition qui est associée à chaque élément dans un conteneur. La figure 5-18 montre comment tous les éléments d’une partition logique ont la même valeur de clé de partition.

![Cosmos DB mécanique du partitionnement](./media/cosmos-db-partitioning.png)

**Figure 5-18**: Cosmos DB mécanique du partitionnement

Notez dans la figure 5-18 comment chaque élément comprend une clé de partition « City » ou « aéroportuaire ». Cette clé de partition détermine la partition logique de l’élément. Chaque code de ville est affecté à une partition logique dans le conteneur situé à gauche et avec un code d’aéroport dans le conteneur situé à droite. La combinaison de la valeur de clé de partition avec la valeur d’ID d’un élément crée l’index de l’élément, qui identifie l’élément de manière unique.

En interne, Cosmos DB gère automatiquement le placement des [partitions logiques](https://docs.microsoft.com/azure/cosmos-db/partition-data) sur les [partitions physiques](https://docs.microsoft.com/azure/cosmos-db/partition-data) pour répondre efficacement aux besoins d’évolutivité et de performances du conteneur. À mesure que le débit et le stockage requis par une application augmentent, Azure Cosmos DB déplace les partitions logiques pour redistribuer la charge sur un plus grand nombre de serveurs. Ces opérations de redistribution sont gérées par Cosmos DB et sont effectuées sans interruption ni temps d’arrêt.

## <a name="azure-redis-cache"></a>Cache Redims Azure

Les avantages de la mise en cache pour améliorer les performances et l’évolutivité sont bien compris.

Pour une application Cloud native, un emplacement commun pour ajouter la mise en cache est à l’intérieur de la passerelle d’API. La passerelle sert de serveur frontal pour toutes les demandes entrantes. En ajoutant la mise en cache, vous pouvez augmenter les performances et la réactivité en retournant les données mises en cache et en évitant les allers-retours vers une base de données locale ou un service en aval. La figure 5-19 illustre une architecture de mise en cache pour une application Cloud native.

![Mise en cache dans une application Cloud Native](./media/caching-in-a-cloud-native-app.png)

**Figure 5-19**: mise en cache dans une application Cloud Native

Un modèle de mise en cache courant est le [modèle cache de réserve](https://docs.microsoft.com/azure/architecture/patterns/cache-aside). Pour une demande entrante, vous interrogez d’abord le cache pour la réponse, comme indiqué à l’étape #1 de la figure 5-19. Si elle est trouvée, les données sont retournées immédiatement. Si les données ne se trouvent pas dans le cache (opération connue sous le nom d’absence dans le [cache](https://www.techopedia.com/definition/6308/cache-miss)), elles sont récupérées à partir de la base de données locale ou du service en aval (étape #2), écrites dans le cache pour les demandes ultérieures (étape #3) et retournées à l’appelant. Vous devez veiller à supprimer régulièrement les données mises en cache afin que le système reste cohérent et précis.

En outre, notez la figure 5-19 Comment le cache n’est pas implémenté localement dans les limites du service, mais qu’il est utilisé en tant que service de sauvegarde Cloud, comme indiqué dans le chapitre 1.

Le [cache redims Azure](https://azure.microsoft.com/services/cache/) est un service de mise en cache des données et de service Broker de messagerie. Il fournit un débit élevé et un accès à faible latence aux données pour les applications. Elle est entièrement gérée par Microsoft, hébergée dans Azure et accessible à toute application au sein ou en dehors d’Azure.

En interne, le cache Azure pour les éléments ReDim est pris en charge par le [serveur ReDim](https://redis.io/) Open source et prend en charge en mode natif des structures de données telles que des [chaînes](https://redis.io/topics/data-types#strings), des [hachages](https://redis.io/topics/data-types#hashes), des [listes](https://redis.io/topics/data-types#sets), des [ensembles](https://redis.io/topics/data-types#sets)et des [ensembles triés](https://redis.io/topics/data-types#sorted-sets). Si votre application utilise des ReDim, elle fonctionnera comme avec le cache Azure pour les opérations ReDim.

Le cache Azure pour les ReDim peut également être utilisé comme un cache de données en mémoire, une base de données non relationnelle distribuée et un courtier de messages. Elle est disponible dans trois niveaux de tarification différents. Le niveau Premium propose de nombreuses fonctionnalités d’entreprise, telles que le clustering, la persistance des données, la géo-réplication et la sécurité et l’isolation des réseaux virtuels.

>[!div class="step-by-step"]
>[Précédent](data-patterns.md)
>[Suivant](resiliency.md)
