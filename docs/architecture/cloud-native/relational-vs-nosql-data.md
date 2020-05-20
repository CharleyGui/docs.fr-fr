---
title: Modèles d'exploration de données relationnels et données NoSQL
description: En savoir plus sur les données relationnelles et NoSQL dans les applications natives du Cloud
author: robvet
ms.date: 05/17/2020
ms.openlocfilehash: cc47faa4fcd4468de9ddc468e488297db4289ff5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613783"
---
# <a name="relational-vs-nosql-data"></a>Modèles d'exploration de données relationnels et données NoSQL

Relationnel et NoSQL sont deux types de systèmes de base de données généralement implémentés dans les applications Cloud natives. Elles sont créées différemment, stockent les données différemment et sont accessibles différemment. Dans cette section, nous allons examiner les deux. Plus loin dans ce chapitre, nous allons examiner une technologie de base de données émergente appelée *NewSQL*.

Les *bases de données relationnelles* ont été une technologie répandue depuis des décennies. Elles sont matures, éprouvées et largement implémentées. Les produits de base de données concurrents, les outils et l’expertise sont nombreux. Les bases de données relationnelles fournissent un magasin de tables de données associées. Ces tables ont un schéma fixe, utilisent SQL (langage SQL) pour gérer les données et prennent en charge les garanties ACID.

*Les bases de données non-SQL* font référence aux banques de données hautes performances et non relationnelles. Ils utilisent Excel dans leurs caractéristiques de facilité d’utilisation, d’évolutivité, de résilience et de disponibilité. Au lieu de joindre des tables de données normalisées, NoSQL stocke des données non structurées ou semi-structurées, souvent dans des paires clé-valeur ou des documents JSON. Les bases de données non-SQL ne fournissent généralement pas de garanties ACID au-delà de la portée d’une seule partition de base de données. Les services de volume élevés qui nécessitent un temps de réponse inférieur à la seconde favorisent les banques de données NoSQL.

L’impact des technologies [NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) pour les systèmes distribués Cloud natifs ne peut pas être surétat. La prolifération des nouvelles technologies de données dans cet espace a perturbé les solutions qui, une fois exclusivement, s’appuyaient sur des bases de données relationnelles.

Les bases de données NoSQL incluent plusieurs modèles différents pour l’accès et la gestion des données, chacun étant adapté à des cas d’usage spécifiques. La figure 5-9 présente quatre modèles communs.

![Modèles de données NoSQL](./media/types-of-nosql-datastores.png)

**Figure 5-9**: modèles de données pour les bases de données NoSQL

| Modèle | Caractéristiques |
| :-------- | :-------- |
| Magasin de documents | Les données et les métadonnées sont stockées hiérarchiquement dans des documents JSON à l’intérieur de la base de données. |
| Magasin de valeurs de clés | La plus simple des bases de données NoSQL, les données sont représentées sous la forme d’une collection de paires clé-valeur. |
| Magasin de colonnes larges | Les données associées sont stockées sous la forme d’un ensemble de paires clé/valeur imbriquées dans une seule colonne. |
| Magasin de graphiques | Les données sont stockées dans une structure graphique en tant que propriétés de nœud, de périphérie et de données. |

## <a name="the-cap-theorem"></a>Le niveau de CAP

Pour comprendre les différences entre ces types de bases de données, tenez compte de l’allocation de CAP, un ensemble de principes appliqués aux systèmes distribués qui stockent l’État. La figure 5-10 montre les trois propriétés de l’embout de CAP.

![Théorème CAP](./media/cap-theorem.png)

**Figure 5-10**. Le niveau de CAP

La valeur de la valeur de l’état des systèmes de données distribués offre un compromis entre la cohérence, la disponibilité et la tolérance de la partition. Et qu’une base de données ne peut garantir que *deux* des trois propriétés suivantes :

- *Cohérence.* Chaque nœud du cluster répond avec les données les plus récentes, même si le système doit bloquer la demande jusqu’à la mise à jour de tous les réplicas. Si vous interrogez un « système cohérent » pour un élément en cours de mise à jour, vous attendez la réponse jusqu’à ce que tous les réplicas soient correctement mis à jour. Toutefois, vous recevrez les données les plus récentes.

- *Sa.* Chaque nœud retourne une réponse immédiate, même si cette réponse n’est pas les données les plus récentes. Si vous interrogez un « système disponible » pour un élément mis à jour, vous obtiendrez la meilleure réponse possible que le service peut fournir à ce moment-là.

- *Tolérance de la partition.* Garantit que le système continue à fonctionner même si un nœud de données répliquées échoue ou perd la connectivité avec d’autres nœuds de données répliqués.

En général, les bases de données relationnelles assurent la cohérence et la disponibilité, mais pas la tolérance de partition. Elles sont généralement approvisionnées sur un serveur unique et sont mises à l’échelle verticalement en ajoutant des ressources supplémentaires à la machine.

De nombreux systèmes de base de données relationnelle prennent en charge des fonctionnalités de réplication intégrées où les copies de la base de données primaire peuvent être effectuées sur d’autres instances de serveur secondaire. Les opérations d’écriture sont effectuées sur l’instance principale et répliquées sur chacun des serveurs secondaires. En cas de défaillance, l’instance principale peut basculer vers une base de données secondaire pour fournir une haute disponibilité. Les secondaires peuvent également être utilisés pour distribuer des opérations de lecture. Tandis que les opérations d’écriture sont toujours effectuées sur le réplica principal, les opérations de lecture peuvent être acheminées vers l’un des serveurs secondaires afin de réduire la charge du système.

Les données peuvent également être partitionnées horizontalement sur plusieurs nœuds, par exemple avec [partitionnement](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction). Toutefois, partitionnement augmente considérablement la charge de traitement des données Spitting sur de nombreux éléments qui ne peuvent pas facilement communiquer. La gestion de peut s’avérer coûteuse et fastidieuse. Cela peut affecter les performances, les jointures de table et l’intégrité référentielle.

Si les réplicas de données perdent la connectivité réseau dans un cluster de base de données relationnelle « hautement cohérent », vous ne seriez pas en mesure d’écrire dans la base de données. Le système rejette l’opération d’écriture, car il ne peut pas répliquer cette modification sur les autres réplicas de données. Chaque réplica de données doit être mis à jour avant que la transaction puisse se terminer.

Les bases de données NoSQL prennent généralement en charge la haute disponibilité et la tolérance de partition. Elles sont mises à l’échelle horizontalement, souvent sur les serveurs de marchandises. Cette approche offre une disponibilité exceptionnelle, à la fois dans et dans les régions géographiques à un coût réduit. Vous partitionnez et répliquez des données sur ces ordinateurs, ou nœuds, pour assurer la redondance et la tolérance de panne. L’inconvénient est la cohérence. Une modification des données sur un nœud NoSQL peut prendre un certain temps pour se propager à d’autres nœuds. En règle générale, un nœud de base de données NoSQL fournit une réponse immédiate à une requête, même si les données présentées sont obsolètes et n’ont pas encore été mises à jour.

Si les réplicas de données perdent la connectivité dans un cluster de base de données NoSQL hautement disponible, vous pouvez toujours effectuer une opération d’écriture dans la base de données. Le cluster de base de données autorise l’opération d’écriture et met à jour chaque réplica de données dès qu’il est disponible.

Ce type de résultat est connu sous le nom de cohérence éventuelle, caractéristique des systèmes de données distribués où les transactions ACID ne sont pas prises en charge. Il s’agit d’un bref délai entre la mise à jour d’un élément de données et le temps nécessaire à la propagation de cette mise à jour à chacun des nœuds de réplica. Dans des conditions normales, le décalage est généralement bref, mais peut augmenter lorsque des problèmes surviennent. Par exemple, que se passerait-il si vous deviez mettre à jour un élément de produit dans une base de données NoSQL dans le États-Unis et interroger ce même élément de données à partir d’un nœud de réplica en Europe ? Vous recevrez les informations précédentes sur le produit jusqu’à ce que le cluster met à jour le nœud européen avec la modification du produit. En renvoyant immédiatement un résultat de requête et sans attendre que tous les nœuds de réplica soient mis à jour, vous obtenez une mise à l’échelle et un volume énormes, mais avec la possibilité de présenter des données plus anciennes.

La haute disponibilité et l’évolutivité massive sont souvent plus importantes pour l’entreprise que la cohérence forte. Les développeurs peuvent implémenter des techniques et des modèles tels que sagas, CQRS et une messagerie asynchrone pour adopter une cohérence éventuelle.

> De nos jours, il convient de veiller à ce que conidering les contraintes de CAP. Un nouveau type de base de données, appelé NewSQL, est apparu, ce qui étend le moteur de base de données relationnelle pour la prise en charge de l’extensibilité horizontale et des performances évolutives des systèmes NoSQL.

## <a name="considerations-for-relational-vs-nosql-systems"></a>Éléments à prendre en considération pour les systèmes relationnels et NoSQL

En fonction des besoins spécifiques des données, un microservice basé sur le Cloud natif peut implémenter une banque de données relationnelles, NoSQL ou les deux.

|  Prenons l’exemple d’une banque de banques NoSQL lorsque : | Prenons l’exemple d’une base de données relationnelle lorsque : |
| :-------- | :-------- |
| Vous avez des charges de travail de volume élevées qui nécessitent une grande échelle | Le volume de votre charge de travail est cohérent et nécessite une échelle moyenne à grande |
| Vos charges de travail n’ont pas besoin de garanties ACID |  Des garanties ACID sont requises |
| Vos données sont dynamiques et changent fréquemment | Vos données sont prévisibles et hautement structurées |
| Les données peuvent être exprimées sans relations | Les données sont mieux exprimées de manière relationnelle |  
| Vous avez besoin d’écritures rapides et la sécurité en écriture n’est pas critique | La sécurité en écriture est obligatoire |  
| La récupération des données est simple et tend à être plate | Vous travaillez avec des requêtes et des rapports complexes|
| Vos données requièrent une répartition géographique étendue | Vos utilisateurs sont plus centralisés |
| Votre application sera déployée sur le matériel de consommation, par exemple avec des clouds publics | Votre application sera déployée sur un matériel haut de gamme. |

Dans les sections suivantes, nous allons explorer les options disponibles dans le Cloud Azure pour le stockage et la gestion de vos données Cloud natives.

## <a name="database-as-a-service"></a>Base de données en tant que service

Pour commencer, vous pouvez approvisionner une machine virtuelle Azure et installer la base de données de votre choix pour chaque service. Bien que vous disposiez d’un contrôle total sur l’environnement, vous devez renoncer à de nombreuses fonctionnalités intégrées de la plateforme Cloud. Vous êtes également responsable de la gestion de la machine virtuelle et de la base de données pour chaque service. Cette approche peut rapidement devenir longue et coûteuse.

Au lieu de cela, les applications Cloud natives favorisent les services de données exposés en tant que [service (DBaaS)](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/). Entièrement gérée par un fournisseur de Cloud, ces services offrent une sécurité, une extensibilité et une surveillance intégrées. Au lieu de détenir le service, il vous suffit de l’utiliser en tant que [service de sauvegarde](./definition.md#backing-services). Le fournisseur opère la ressource à l’échelle et assume la responsabilité des performances et de la maintenance.

Ils peuvent être configurés dans des zones de disponibilité du Cloud et des régions pour obtenir une haute disponibilité. Ils prennent tous en charge la capacité juste-à-temps et un modèle de paiement à l’accès. Azure propose différents types d’options de service de données gérées, chacune avec des avantages spécifiques.

Nous allons tout d’abord examiner les services DBaaS relationnels disponibles dans Azure. Vous verrez que la base de données phare de Microsoft SQL Server est disponible, ainsi que plusieurs options Open source. Ensuite, nous parlerons des services de données NoSQL dans Azure.

## <a name="azure-relational-databases"></a>Bases de données relationnelles Azure

Pour les microservices Cloud natifs qui requièrent des données relationnelles, Azure propose quatre offres relationnelles gérées en tant que service (DBaaS), comme illustré à la figure 5-11.

![Bases de données relationnelles gérées dans Azure](./media/azure-managed-databases.png)

**Figure 5-11**. Bases de données relationnelles gérées disponibles dans Azure

Dans la figure précédente, Notez comment chacun d’entre eux repose sur une infrastructure DBaaS commune qui offre des fonctionnalités clés sans coût supplémentaire.

Ces fonctionnalités sont particulièrement importantes pour les organisations qui approvisionnent un grand nombre de bases de données, mais qui ont des ressources limitées pour les administrer.
Vous pouvez approvisionner une base de données Azure en quelques minutes en sélectionnant la quantité de cœurs de traitement, la mémoire et le stockage sous-jacent. Vous pouvez mettre à l’échelle la base de données à la volée et ajuster dynamiquement les ressources avec peu ou pas de temps d’arrêt.

## <a name="azure-sql-database"></a>Azure SQL Database

Les équipes de développement ayant une expertise dans Microsoft SQL Server doivent prendre en compte [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/). Il s’agit d’une base de données relationnelle en tant que service (DBaaS) entièrement managée basée sur la Moteur de base de données Microsoft SQL Server. Le service partage de nombreuses fonctionnalités qui se trouvent dans la version locale de SQL Server et exécute la dernière version stable du SQL Server Moteur de base de données.

Pour une utilisation avec un microservice Cloud natif, Azure SQL Database est disponible avec trois options de déploiement :

- Un base de données unique représente une SQL Database entièrement gérée exécutée sur un [serveur Azure SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-servers) dans le Cloud Azure. La base de données est considérée comme [*contenue*](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) , car elle n’a aucune dépendance de configuration sur le serveur de base de données sous-jacent.
  
- Une [Managed instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) est une instance entièrement gérée du moteur de base de données Microsoft SQL Server qui fournit une compatibilité presque de 100% avec un SQL Server local. Cette option prend en charge les bases de données plus volumineuses, jusqu’à 35 to, et est placée dans un [réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) pour une meilleure isolation.

- [Azure SQL Database sans serveur](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) est un niveau de calcul pour une base de données unique qui est automatiquement mise à l’échelle en fonction de la demande de la charge de travail. Elle facture uniquement la quantité de calcul utilisée par seconde. Le service est bien adapté aux charges de travail avec des modèles d’utilisation intermittents et imprévisibles, intercalés avec des périodes d’inactivité. Le niveau de calcul sans serveur suspend également automatiquement les bases de données pendant les périodes inactives afin que seuls les frais de stockage soient facturés. Il reprend automatiquement lorsque l’activité est retournée.

Au-delà de la pile de Microsoft SQL Server traditionnelle, Azure propose également des versions gérées de trois bases de données Open source populaires.

## <a name="open-source-databases-in-azure"></a>Bases de données Open source dans Azure

Les bases de données relationnelles Open source sont devenues des choix populaires pour les applications Cloud natives. De nombreuses entreprises privilégient les produits de base de données commerciaux, en particulier pour les économies. De nombreuses équipes de développement bénéficient de leur flexibilité, du développement de la communauté et de l’écosystème des outils et extensions. Les bases de données Open source peuvent être déployées sur plusieurs fournisseurs de Cloud, ce qui contribue à réduire le problème de « verrouillage des fournisseurs ».

Les développeurs peuvent facilement héberger n’importe quelle base de données Open source sur une machine virtuelle Azure. En fournissant un contrôle total, cette approche vous place sur le hook pour la gestion, la surveillance et la maintenance de la base de données et de la machine virtuelle.

Toutefois, Microsoft poursuit son engagement à conserver Azure une « plateforme ouverte » en proposant plusieurs bases de données Open source populaires en tant que services DBaaS *entièrement gérés* .

### <a name="azure-database-for-mysql"></a>Azure Database pour MySQL

[MySQL](https://en.wikipedia.org/wiki/MySQL)   est une base de données relationnelle Open source et un pilier pour les applications basées sur la [pile de logiciels LAMP](https://en.wikipedia.org/wiki/LAMP_(software_bundle)). Largement choisi pour les charges de travail volumineuses *en lecture* , il est utilisé par de nombreuses grandes organisations, notamment Facebook, Twitter et YouTube. L’édition Community est disponible gratuitement, tandis que l’édition Enterprise requiert un achat de licence. Initialement créé dans 1995, le produit a été acheté par Sun Microsystems dans 2008. Oracle a acquis Sun et MySQL en 2010.

[Azure Database pour MySQL](https://azure.microsoft.com/services/mysql/) est un service de base de données relationnelle géré basé sur le moteur Open source MySQL Server. Il utilise l’édition Community de MySQL. Le serveur Azure MySQL est le point d’administration du service. Il s’agit du même moteur MySQL Server utilisé pour les déploiements sur site. Le moteur peut créer une base de données unique par serveur ou plusieurs bases de données par serveur qui partagent des ressources. Vous pouvez continuer à gérer les données à l’aide des mêmes outils open source sans avoir à acquérir de nouvelles compétences ni à gérer des machines virtuelles.

### <a name="azure-database-for-mariadb"></a>Azure Database for MariaDB

[MariaDB](https://mariadb.com/) Le serveur est un autre serveur de base de données Open source populaire. Il a été créé en tant que *fourche* de MySQL quand Oracle a acheté Sun Microsystems, qui détenait MySQL. L’objectif était de s’assurer que MariaDB restait Open source. Comme MariaDB est une fourche de MySQL, les définitions de données et de table sont compatibles, et les protocoles, structures et API du client sont à la fois étroits.

MariaDB a une communauté forte et est utilisée par de nombreuses grandes entreprises. Bien qu’Oracle continue à gérer, améliorer et prendre en charge MySQL, MariaDB Foundation gère MariaDB, ce qui permet d’effectuer des contributions publiques au produit et à la documentation.

[Azure Database for MariaDB](https://azure.microsoft.com/services/mariadb/) est une base de données relationnelle entièrement gérée en tant que service dans le Cloud Azure. Le service est basé sur le moteur du serveur MariaDB Community Edition. Il peut gérer les charges de travail critiques avec des performances prévisibles et une évolutivité dynamique.

### <a name="azure-database-for-postgresql"></a>Azure Database pour PostgreSQL

[PostgreSQL](https://www.postgresql.org/) est une base de données relationnelle Open source avec plus de 30 ans de développement actif. PostgresSQL a une réputation forte pour la fiabilité et l’intégrité des données. Elle est riche en fonctionnalités, conforme à SQL et considérée comme plus performante que MySQL, en particulier pour les charges de travail avec des requêtes complexes et des écritures lourdes. De nombreuses grandes entreprises, dont Apple, Red Hat et Fujitsu, ont créé des produits à l’aide de PostgreSQL.

[Azure Database pour PostgreSQL](https://azure.microsoft.com/services/postgresql/) est un service de base de données relationnelle entièrement géré, basé sur le moteur de base de données postgres Open source. Le service prend en charge de nombreuses plateformes de développement, notamment C++, Java, Python, Node, C \# et php. Vous pouvez migrer des bases de données PostgreSQL à l’aide de l’outil d' [interface de ligne de commande](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) ou du service de migration de données Azure.

La base de données Azure pour PostgreSQL est disponible avec deux options de déploiement :

- L’option de déploiement de [serveur unique](https://docs.microsoft.com/azure/postgresql/concepts-servers) est un point d’administration central pour plusieurs bases de données sur lesquelles vous pouvez déployer de nombreuses bases de données. La tarification est structurée par serveur en fonction des cœurs et du stockage.

- L' [option hyperscale (CITUS)](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) est optimisée par la technologie de données CITUS. Il offre des performances élevées grâce à la *mise à l’échelle horizontale* d’une base de données sur des centaines de nœuds pour fournir des performances et une évolutivité rapides. Cette option permet au moteur d’intégrer plus de données en mémoire, de paralléliser les requêtes sur des centaines de nœuds et d’indexer les données plus rapidement.

## <a name="nosql-data-in-azure"></a>Données NoSQL dans Azure

Cosmos DB est un service de base de données NoSQL entièrement géré et distribué à l’échelle mondiale dans le Cloud Azure. Il a été adopté par de nombreuses grandes entreprises dans le monde entier, notamment Coca-Cola, Skype, ExxonMobil et Liberty.

Si vos services nécessitent une réponse rapide depuis n’importe où dans le monde, une haute disponibilité ou une évolutivité élastique, Cosmos DB est un bon choix. La figure 5-12 montre Cosmos DB.

![Vue d’ensemble de Cosmos DB](./media/cosmos-db-overview.png)

**Figure 5-12**: vue d’ensemble des Cosmos DB

La figure précédente présente un grand nombre des fonctionnalités Cloud natives intégrées disponibles dans Cosmos DB. Dans cette section, nous examinerons les détails.

### <a name="global-support"></a>Support global

Les applications Cloud natives ont souvent un public international et nécessitent une mise à l’échelle globale.

Vous pouvez distribuer des bases de données Cosmos dans des régions ou dans le monde entier, en plaçant les données à proximité de vos utilisateurs, en améliorant le temps de réponse et en réduisant la latence. Vous pouvez ajouter ou supprimer une base de données d’une région sans interrompre ou redéployer vos services. En arrière-plan, Cosmos DB réplique en toute transparence les données dans chacune des régions configurées.

Cosmos DB prend en charge le clustering [actif/actif](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) au niveau global, ce qui vous permet de configurer toutes les régions de votre base de données pour prendre en charge *les écritures et les lectures*.

Le protocole [multimaître](https://docs.microsoft.com/azure/cosmos-db/multi-master-benefits) est une fonctionnalité importante de Cosmos DB qui active les fonctionnalités suivantes :

- Bénéficier d’une évolutivité élastique illimitée en écriture et en lecture.

- Disponibilité en lecture et en écriture de 99,999 % dans le monde entier.

- Lectures et écritures traitées en moins de 10 millisecondes au 99e centile.

Avec la Cosmos DB les [API d’hébergement multiple](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), votre microservice connaît automatiquement la région Azure la plus proche et lui envoie des requêtes. La région la plus proche est identifiée par Cosmos DB sans aucune modification de configuration. Si une région n’est plus disponible, la fonctionnalité d’hébergement multiple achemine automatiquement les demandes vers la région disponible la plus proche.

### <a name="multi-model-support"></a>Prise en charge de plusieurs modèles

En cas de changement de plate-forme d’applications monolithiques dans une architecture Cloud native, les équipes de développement doivent parfois migrer des magasins de données NoSQL Open source. Cosmos DB peut vous aider à conserver votre investissement dans ces banques de données NoSQL avec sa plateforme de données *multimodèle* . Le tableau suivant présente les API de [compatibilité](https://www.wikiwand.com/en/Cosmos_DB)NoSQL prises en charge.

| Fournisseur | Description  |
| :-------- | :-------- |
| API SQL | API propriétaire qui prend en charge les documents JSON et les requêtes basées sur SQL |
| API MongoDB | Prend en charge les API Mongo DB et les documents JSON|
| API Gremlin | Prend en charge l’API Gremlin avec des nœuds basés sur des graphiques et des représentations de données de périphérie |
| API Cassandra | Prend en charge l’API Casandra pour les représentations de données à grande colonne |  
| API de table  | Prend en charge le stockage de tables Azure avec des améliorations Premium |  
| API ETCD | Active Cosmos DB en tant que magasin de stockage pour les clusters de service Azure Kubernetes |

Les équipes de développement peuvent migrer des bases de données Mongo, Gremlin ou Cassandra existantes dans Cosmos DB avec des modifications minimes des données ou du code. Pour les nouvelles applications, les équipes de développement peuvent choisir parmi les options Open source ou le modèle d’API SQL intégré.

> En interne, Cosmos stocke les données dans un format de struct simple constitué de types de données primitifs. Pour chaque demande, le moteur de base de données traduit les données primitives dans la représentation du modèle que vous avez sélectionnée.

Dans le tableau précédent, notez l’option [API table](https://docs.microsoft.com/azure/cosmos-db/table-introduction) . Cette API est une évolution du stockage de tables Azure. Les deux partagent le même modèle de table sous-jacent, mais le Cosmos DB API Table ajoute des améliorations Premium non disponibles dans l’API Azure Storage. Le tableau suivant compare les fonctionnalités.

|  | Stockage de table Azure  | Azure Cosmos DB  |
| :-------- | :-------- |:-------- |
| Latence | Rapide | Latence à un chiffre en millisecondes pour les lectures et écritures n’importe où dans le monde |
| Débit | Limite de 20 000 opérations par table | 10 millions opérations par table |
| Diffusion mondiale | Une seule région avec une seule région de lecture secondaire facultative | Distributions clé en main vers toutes les régions avec basculement automatique |
| Indexation | Disponible pour les propriétés de clé de partition et de ligne uniquement | Indexation automatique de toutes les propriétés |
| Tarifs | Basé sur le stockage | En fonction du débit |

Les microservices qui utilisent le stockage table Azure peuvent facilement migrer vers le API Table Cosmos DB. Le code n’a pas besoin d’être modifié.

### <a name="tunable-consistency"></a>Cohérence réglable

Plus haut dans la section *relationnelle et NoSQL* , nous avons abordé l’objet de la *cohérence des données*. La cohérence des données fait référence à l' *intégrité* de vos données. Les services Cloud-natives avec des données distribuées reposent sur la réplication et doivent faire un compromis fondamental entre cohérence des lectures, disponibilité et latence.

La plupart des bases de données distribuées permettent aux développeurs de choisir entre deux modèles de cohérence : une cohérence forte et une cohérence éventuelle. Une *cohérence forte* est la norme Gold de la programmabilité des données. Elle garantit qu’une requête renverra toujours les données les plus récentes, même si le système doit subir une latence en attendant la réplication d’une mise à jour sur toutes les copies de base de données. Alors qu’une base de données configurée pour *la cohérence éventuelle* retourne des données immédiatement, même si ces données ne sont pas la copie la plus récente. Cette dernière option permet une disponibilité plus élevée, une mise à l’échelle supérieure et des performances accrues.

Azure Cosmos DB propose cinq [modèles de cohérence](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) bien définis illustrés dans la figure 5-13.

![Graphique de cohérence des Cosmos DB](./media/cosmos-consistency-level-graph.png)

**Figure 5-13**: Cosmos DB niveaux de cohérence

 Ces options vous permettent d’effectuer des choix précis et des compromis granulaires pour la cohérence, la disponibilité et les performances de vos données. Les niveaux sont présentés dans le tableau suivant.

| Niveau de cohérence | Description  |
| :-------- | :-------- |
| Eventual (Éventuel) | Aucune garantie de classement pour les lectures. Les réplicas finiront par converger. |
| Préfixe de constante | Les lectures sont toujours éventuelles, mais les données sont retournées dans l’ordre dans lequel elles sont écrites. |
| session | Garantit que vous pouvez lire toutes les données écrites pendant la session active. Il s’agit du niveau de cohérence par défaut. |
| Obsolescence limitée | Lit les écritures de trace par intervalle que vous spécifiez. |  
| Remarque  | Il est garanti que les lectures renvoient la version la plus récente d’un élément. Un client ne voit jamais de lecture partielle ou non validée. |  

Dans l’article en [arrière-plan des niveaux de cohérence 9 Ball : Cosmos DB expliqués](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/), le gestionnaire de programmes Microsoft Jeremy Likness fournit une excellente explication des cinq modèles.

### <a name="partitioning"></a>Partitionnement

Azure Cosmos DB prend en charge le [partitionnement](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) automatique pour mettre à l’échelle une base de données afin de répondre aux besoins de performances de vos services Cloud natifs.

Vous gérez les données de Cosmos DB données en créant des bases de données, des conteneurs et des éléments.

Les conteneurs vivent dans une base de données Cosmos DB et représentent un regroupement d’éléments indépendant du schéma. Les éléments sont les données que vous ajoutez au conteneur. Elles sont représentées sous forme de documents, de lignes, de nœuds ou d’arêtes. Tous les éléments ajoutés à un conteneur sont automatiquement indexés.

Pour partitionner le conteneur, les éléments sont divisés en sous-ensembles distincts appelés partitions logiques. Les partitions logiques sont renseignées en fonction de la valeur d’une clé de partition qui est associée à chaque élément dans un conteneur. La figure 5-14 montre deux conteneurs, chacun avec une partition logique basée sur une valeur de clé de partition.

![Cosmos DB mécanique du partitionnement](./media/cosmos-db-partitioning.png)

**Figure 5-14**: Cosmos DB mécanique du partitionnement

Notez dans la figure précédente comment chaque élément comprend une clé de partition « City » ou « aéroportuaire ». La clé détermine la partition logique de l’élément. Les éléments avec un code de ville sont affectés au conteneur à gauche et aux éléments avec un code d’aéroport, au conteneur situé à droite. La combinaison de la valeur de clé de partition avec la valeur d’ID crée l’index d’un élément, qui identifie l’élément de manière unique.

En interne, Cosmos DB gère automatiquement le placement des [partitions logiques](https://docs.microsoft.com/azure/cosmos-db/partition-data) sur les partitions physiques pour répondre aux besoins d’évolutivité et de performances du conteneur. À mesure que les besoins en termes de débit et de stockage des applications augmentent, Azure Cosmos DB redistribue les partitions logiques sur un plus grand nombre de serveurs. Les opérations de redistribution sont gérées par Cosmos DB et appelées sans interruption ni temps d’arrêt.

## <a name="newsql-databases"></a>Bases de données NewSQL

*NewSQL*   est une technologie de base de données émergente qui combine l’extensibilité distribuée de NoSQL avec les garanties ACID d’une base de données relationnelle. Les bases de données NewSQL sont importantes pour les systèmes d’entreprise qui doivent traiter de gros volumes de données, dans des environnements distribués, avec une prise en charge de transactions complète et une conformité ACID. Bien qu’une base de données NoSQL puisse fournir une évolutivité massive, elle ne garantit pas la cohérence des données. Des problèmes intermittents de données incohérentes peuvent compliquer l’équipe de développement. Les développeurs doivent créer des protections dans leur code de microservice pour gérer les problèmes provoqués par des données incohérentes.

CNCF (Cloud Native Computing Foundation) propose plusieurs projets de base de données NewSQL.

| Projet | Caractéristiques |
| :-------- | :-------- |
| Cockroach DB |Une base de données relationnelle compatible ACID qui évolue globalement. Ajoutez un nouveau nœud à un cluster et CockroachDB s’occupe de l’équilibrage des données entre les instances et les zones géographiques. Il crée, gère et distribue les réplicas pour garantir la fiabilité. Il est open source et disponible gratuitement.  |
| TiDB | Une base de données Open source qui prend en charge les charges de travail hybrides de traitement transactionnel et analytique (HTAP). Il est compatible avec MySQL et propose une extensibilité horizontale, une cohérence forte et une haute disponibilité.  TiDB agit comme un serveur MySQL. Vous pouvez continuer à utiliser les bibliothèques clientes MySQL existantes, sans avoir à modifier l’intégralité du code de votre application. |
| YugabyteDB | Une base de données SQL distribuée, hautement performante et open source. Il prend en charge la faible latence des requêtes, la résilience contre les défaillances et la distribution globale des données. YugabyteDB est compatible avec PostgressSQL et gère les charges de travail OLTP avec montée en charge et à l’échelle d’Internet. Le produit prend également en charge NoSQL et est compatible avec Cassandra. |
|Vitess | Vitess est une solution de base de données pour le déploiement, la mise à l’échelle et la gestion de grands clusters d’instances MySQL. Il peut s’exécuter dans une architecture de cloud privé ou public. Vitess combine et étend de nombreuses fonctionnalités et fonctionnalités MySQL importantes en matière de prise en charge des partitionnement verticales et horizontales. Provient de YouTube, vitess a servi tout le trafic de la base de données YouTube depuis 2011. |

Les projets open source de la figure précédente sont disponibles à partir de la Fondation Cloud Native Computing. Trois de ces offres sont des produits de base de données complets, qui incluent la prise en charge de .NET Core. L’autre, vitess, est un système de mise en cluster de bases de données qui met horizontalement à l’échelle des clusters volumineux d’instances MySQL.

L’un des principaux objectifs de conception pour les bases de données NewSQL consiste à travailler en mode natif dans Kubernetes, en tirant parti de la résilience et de l’évolutivité de la plateforme.

Les bases de données NewSQL sont conçues pour prospérer dans les environnements Cloud éphémères dans lesquels les machines virtuelles sous-jacentes peuvent être redémarrées ou replanifiées à un moment donné. Les bases de données sont conçues pour survivre aux défaillances de nœud sans perte de données ni temps d’arrêt. CockroachDB, par exemple, peut survivre à une perte d’ordinateur en conservant trois réplicas cohérents de toutes les données sur les nœuds d’un cluster.

Kubernetes utilise une *construction de services* pour permettre à un client d’adresser un groupe de processus de bases de données NewSQL identiques à partir d’une seule entrée DNS. En dissociant les instances de base de données de l’adresse du service auquel elle est associée, nous pouvons mettre à l’échelle sans interrompre les instances existantes de l’application. L’envoi d’une demande à un service à un moment donné produira toujours le même résultat.

Dans ce scénario, toutes les instances de base de données sont égales. Il n’existe pas de relations principales ou secondaires. Les techniques telles que *la réplication par consensus* dans CockroachDB permettent à n’importe quel nœud de base de données de traiter n’importe quelle demande. Si le nœud qui reçoit une demande d’équilibrage de charge dispose des données dont il a besoin localement, il répond immédiatement. Si ce n’est pas le cas, le nœud devient une passerelle et transfère la demande aux nœuds appropriés pour obtenir la réponse correcte. Du point de vue du client, chaque nœud de base de données est identique : ils apparaissent sous la forme d’une base de données *logique* unique avec les garanties de cohérence d’un système à un seul ordinateur, malgré des dizaines voire des centaines de nœuds qui fonctionnent en arrière-plan.

Pour obtenir une vue détaillée de la mécanique des bases de données NewSQL, consultez l’article [Dash : quatre propriétés de Kubernetes-bases de données natives](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/) .

## <a name="data-migration-to-the-cloud"></a>Migration des données vers le Cloud

L’une des tâches les plus fastidieuses consiste à migrer des données d’une plate-forme de données vers une autre. Le [service de migration de données Azure](https://azure.microsoft.com/services/database-migration/) peut aider à accélérer ces efforts. Il peut migrer des données à partir de plusieurs sources de base de données externes vers des plateformes de données Azure avec un temps d’arrêt minimal. Les plateformes cibles incluent les services suivants :

- Azure SQL Database
- Azure Database pour MySQL
- Azure Database for MariaDB
- Azure Database pour PostgreSQL
- CosmosDB
  
Le service fournit des recommandations qui vous guident à travers les modifications nécessaires pour exécuter une migration, à la fois petite ou grande.

>[!div class="step-by-step"]
>[Précédent](distributed-data.md) 
> [Suivant](azure-caching.md)
