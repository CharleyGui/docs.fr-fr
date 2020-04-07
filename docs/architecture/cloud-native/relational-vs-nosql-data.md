---
title: Modèles d'exploration de données relationnels et données NoSQL
description: Renseignez-vous sur les données relationnelles et NoSQL dans les applications cloud-native
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: 3fb3dcc3a87e278c05f3e15d261245f4d61453d1
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805805"
---
# <a name="relational-vs-nosql-data"></a>Modèles d'exploration de données relationnels et données NoSQL

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Relationnel et NoSQL sont deux types de systèmes de base de données couramment mis en œuvre dans les applications cloud-natives. Ils sont construits différemment, stockent les données différemment et sont consultés différemment. Dans cette section, nous allons examiner les deux. Plus tard dans ce chapitre, nous examinerons une nouvelle technologie de base de données appelée *NewSQL*.

*Les bases de données relationnelles* sont une technologie répandue depuis des décennies. Ils sont matures, éprouvés et largement mis en œuvre. Les produits de base de données concurrents, l’outillage et l’expertise abondent. Les bases de données relationnelles fournissent un stock de tableaux de données connexes. Ces tables ont un schéma fixe, utilisent SQL (Langage de requête structurée) pour gérer les données et prennent en charge les garanties ACID.

*Les bases de données no-SQL* font référence à des magasins de données non relationnels à haut rendement. Ils excellent dans leur facilité d’utilisation, leur évolutivité, leur résilience et leurs caractéristiques de disponibilité. Au lieu de joindre des tableaux de données normalisées, NoSQL stocke des données non structurées ou semi-structurées, souvent dans des paires de valeurs clés ou des documents JSON. Les bases de données No-SQL ne fournissent généralement pas de garanties ACID au-delà de la portée d’une seule partition de base de données. Les services à volume élevé qui nécessitent un temps de réponse sous la seconde favorisent les datastores NoSQL.

On ne peut exagérer l’impact des technologies [NoSQL](https://www.geeksforgeeks.org/introduction-to-nosql/) pour les systèmes cloud-autochtones distribués. La prolifération des nouvelles technologies de données dans cet espace a perturbé des solutions qui reposaient autrefois exclusivement sur des bases de données relationnelles.

Les bases de données NoSQL comprennent plusieurs modèles différents pour accéder et gérer les données, chacune adaptée à des cas d’utilisation spécifiques. La figure 5-9 présente quatre modèles communs.

![Modèles de données NoSQL](./media/types-of-nosql-datastores.png)

**Figure 5-9**: Modèles de données pour les bases de données NoSQL

| Modèle | Caractéristiques |
| :-------- | :-------- |
| Magasin de documents | Les données et les métadonnées sont stockées hiérarchiquement dans des documents basés sur JSON à l’intérieur de la base de données. |
| Boutique de valeur clé | Plus simple des bases de données NoSQL, les données sont représentées comme une collection de paires de valeurs clés. |
| Magasin à colonnes larges | Les données connexes sont stockées sous forme d’un ensemble de paires de clés imbriquées/valeur dans une seule colonne. |
| Graphique Store | Les données sont stockées dans une structure graphique sous forme de nœuds, de bords et de propriétés de données. |

## <a name="the-cap-theorem"></a>Le théorème de la PAC

Comme un moyen de comprendre les différences entre ces types de bases de données, considérez le théorème de la PAC, un ensemble de principes appliqués aux systèmes distribués qui stockent l’état. La figure 5-10 montre les trois propriétés du théorème du PAC.

![Théorème CAP](./media/cap-theorem.png)

**Figure 5-10**. Le théorème de la PAC

Le théorème indique que les systèmes de données distribués offriront un compromis entre la cohérence, la disponibilité et la tolérance à la partition. Et, que toute base de données ne peut garantir *que deux* des trois propriétés:

- *Cohérence.* Chaque nœud dans le cluster répond avec les données les plus récentes, même si le système doit bloquer la demande jusqu’à ce que toutes les répliques mettent à jour. Si vous interrogez un « système cohérent » pour un élément qui est actuellement mis à jour, vous attendrez cette réponse jusqu’à ce que toutes les répliques mettent à jour avec succès. Toutefois, vous recevrez les données les plus récentes.

- *Disponibilité.* Chaque nœud renvoie une réponse immédiate, même si cette réponse n’est pas les données les plus récentes. Si vous interrogez un « système disponible » pour un élément qui est mis à jour, vous obtiendrez la meilleure réponse possible que le service peut fournir à ce moment..

- *Tolérance de partition.* Garantit que le système continue de fonctionner même si un nœud de données répliqué échoue ou perd la connectivité avec d’autres nœuds de données répliqués.

Les bases de données relationnelles fournissent généralement la cohérence et la disponibilité, mais pas la tolérance de partition. Ils sont généralement provisionnés à un seul serveur et l’échelle verticalement en ajoutant plus de ressources à la machine.

De nombreux systèmes de base de données relationnels prennent en charge les fonctionnalités de réplication intégrées où des copies de la base de données primaire peuvent être faites à d’autres instances secondaires du serveur. Les opérations d’écriture sont faites à l’instance primaire et répliquées à chacun des secondaires. Lors d’un échec, l’instance primaire peut échouer à un secondaire pour fournir une grande disponibilité. Les secondaires peuvent également être utilisés pour distribuer des opérations de lecture. Bien que les opérations d’écriture vont toujours à l’encontre de la réplique primaire, les opérations de lecture peuvent être acheminées à l’un des secondaires pour réduire la charge du système.

Les données peuvent également être divisées horizontalement entre plusieurs nœuds, comme avec [des éclats.](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction) Mais, l’éclat augmente considérablement les frais généraux opérationnels en crachant des données sur de nombreux morceaux qui ne peuvent pas facilement communiquer. Il peut être coûteux et long à gérer. Il peut avoir un impact sur les performances, les jointures de table et l’intégrité référentielle.

Si les répliques de données perdaient la connectivité réseau dans un cluster de base de données relationnel « hautement cohérent », vous ne seriez pas en mesure d’écrire à la base de données. Le système rejetterait l’opération d’écriture car il ne peut pas reproduire ce changement à l’autre réplique de données. Chaque réplique de données doit être mise à jour avant que la transaction ne puisse être terminée.

Les bases de données NoSQL prennent généralement en charge la haute disponibilité et la tolérance à la partition. Ils s’étendent horizontalement, souvent à travers les serveurs de marchandises. Cette approche offre une grande disponibilité, tant à l’intérieur qu’entre les régions géographiques à un coût réduit. Vous divisez et reproduisez des données entre ces machines, ou nœuds, fournissant la redondance et la tolérance aux défauts. L’inconvénient est la cohérence. Un changement de données sur un nœud NoSQL peut prendre un certain temps pour se propager à d’autres nœuds. En règle générale, un nœud de base de données NoSQL fournira une réponse immédiate à une requête - même si les données qui sont présentées sont périmées et n’a pas encore mis à jour.

Si les répliques de données perdaient la connectivité dans un cluster de base de données NoSQL « hautement disponible », vous pouvez tout de même effectuer une opération d’écriture à la base de données. Le cluster de base de données permettrait l’opération de rédaction et mettre à jour chaque réplique de données dès qu’elle sera disponible.

Ce type de résultat est connu sous le nom de cohérence éventuelle, une caractéristique des systèmes de données distribués où les transactions ACID ne sont pas prises en charge. Il s’agit d’un bref délai entre la mise à jour d’un élément de données et le temps qu’il faut pour propager cette mise à jour à chacun des nœuds réplique. Dans des conditions normales, le décalage est généralement court, mais peut augmenter lorsque des problèmes surgissent. Par exemple, que se passerait-il si vous mettiez à jour un article produit dans une base de données NoSQL aux États-Unis et interrogez ce même élément de données à partir d’un nœud réplique en Europe? Vous recevrez les informations de produit antérieures, jusqu’à ce que le cluster met à jour le nœud européen avec le changement de produit. En retournant immédiatement un résultat de requête et en n’attendant pas que tous les nœuds répliques mettent à jour, vous gagnez une échelle et un volume énormes, mais avec la possibilité de présenter des données plus anciennes.

La grande disponibilité et l’évolutivité massive sont souvent plus critiques pour l’entreprise qu’une forte cohérence. Les développeurs peuvent mettre en œuvre des techniques et des modèles tels que Sagas, CQRS, et la messagerie asynchrone pour embrasser la cohérence éventuelle.

> Aujourd’hui, il faut faire attention à la conidering des contraintes de théorème de la PAC. Un nouveau type de base de données, appelé NewSQL, a vu le jour, qui étend le moteur de base de données relationnel pour prendre en charge à la fois l’évolutivité horizontale et les performances évolutives des systèmes NoSQL.

## <a name="considerations-for-relational-vs-nosql-systems"></a>Considérations relatives aux systèmes relationnels par rapport aux systèmes NoSQL

Selon des exigences spécifiques en matière de données, un microservice basé sur le cloud peut implémenter un magasin de données noSQL relationnel ou les deux.

|  Considérez une datastore NoSQL lorsque : | Considérez une base de données relationnelle lorsque : |
| :-------- | :-------- |
| Vous avez une charge de travail à volume élevé qui exige une grande échelle | Votre volume de charge de travail est constant et nécessite des |
| Vos charges de travail ne nécessitent pas de garanties ACID |  Des garanties ACID sont requises |
| Vos données sont dynamiques et changent fréquemment | Vos données sont prévisibles et très structurées |
| Les données peuvent être exprimées sans relations | Les données sont mieux exprimées relationnellement |  
| Vous avez besoin d’écrits rapides et écrire la sécurité n’est pas critique | Écrire la sécurité est une exigence |  
| La récupération des données est simple et a tendance à être plate | Vous travaillez avec des requêtes et des rapports complexes|
| Vos données nécessitent une large répartition géographique | Vos utilisateurs sont plus centralisés |
| Votre application sera déployée sur le matériel de marchandises, comme avec des nuages publics | Votre application sera déployée sur de grands matériels haut de gamme |
|||

Dans les sections suivantes, nous explorerons les options disponibles dans le cloud Azure pour stocker et gérer vos données cloud-natives.

## <a name="database-as-a-service"></a>Base de données en tant que service

Pour commencer, vous pouvez fournir une machine virtuelle Azure et installer votre base de données de choix pour chaque service. Bien que vous ayez un contrôle total sur l’environnement, vous renonceriez à de nombreuses fonctionnalités intégrées de la plate-forme cloud. Vous seriez également responsable de la gestion de la machine virtuelle et de la base de données pour chaque service. Cette approche pourrait rapidement prendre beaucoup de temps et coûter cher.

Au lieu de cela, les applications cloud-native favorisent les services de données exposés comme une [base de données comme un service (DBaaS)](https://www.stratoscale.com/blog/dbaas/what-is-database-as-a-service/). Entièrement gérés par un fournisseur de cloud, ces services assurent une sécurité intégrée, une évolutivité et une surveillance. Au lieu de posséder le service, vous le consommez simplement comme un [service d’accompagnement](./definition.md#backing-services). Le fournisseur exploite la ressource à grande échelle et assume la responsabilité du rendement et de l’entretien.

Ils peuvent être configurés à travers les zones de disponibilité du cloud et les régions pour atteindre une grande disponibilité. Ils prennent tous en charge la capacité juste-à-temps et un modèle de pay-as-you-go. Azure propose différents types d’options de service de données gérées, chacune avec des avantages spécifiques.

Nous allons d’abord examiner les services DBaaS relationnels disponibles à Azure. Vous verrez que la base de données SQL Server phare de Microsoft est disponible avec plusieurs options open-source. Ensuite, nous parlerons des services de données NoSQL à Azure.

## <a name="azure-relational-databases"></a>Bases de données relationnelles Azure

Pour les microservices natifs du cloud qui nécessitent des données relationnelles, Azure offre quatre bases de données relationnelles gérées en tant que service (DBaaS), indiquées dans la figure 5-11.

![Bases de données relationnelles gérées à Azure](./media/azure-managed-databases.png)

**Figure 5-11**. Bases de données relationnelles gérées disponibles en Azure

Dans le chiffre précédent, notez comment chacun se trouve sur une infrastructure DBaaS commune qui dispose de capacités clés sans frais supplémentaires.

Ces caractéristiques sont particulièrement importantes pour les organisations qui disposent d’un grand nombre de bases de données, mais qui ont des ressources limitées pour les administrer.
Vous pouvez fournir une base de données Azure en quelques minutes en sélectionnant la quantité de cœurs de traitement, de mémoire et de stockage sous-jacent. Vous pouvez mettre à l’échelle la base de données à la volée et ajuster dynamiquement les ressources avec peu ou pas de temps d’arrêt.

## <a name="azure-sql-database"></a>Azure SQL Database

Les équipes de développement ayant une expertise dans Microsoft SQL Server devraient envisager [Azure SQL Database](https://docs.microsoft.com/azure/sql-database/). Il s’agit d’une base de données relationnelle entièrement gérée en tant que service (DBaaS) basée sur le moteur de base de données Microsoft SQL Server Database Engine. Le service partage de nombreuses fonctionnalités trouvées dans la version sur place de SQL Server et exécute la dernière version stable du moteur de base de données de serveur SQL.

Pour une utilisation avec un microservice natif du cloud, Azure SQL Database est disponible avec trois options de déploiement :

- Une base de données unique représente une base de données SQL entièrement gérée fonctionnant sur un [serveur de base de données SqL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-servers) dans le cloud Azure. La base de données est considérée comme [*contenue*](https://docs.microsoft.com/sql/relational-databases/databases/contained-databases) car elle n’a aucune dépendance de configuration sur le serveur de base de données sous-jacent.
  
- Une [instance gérée](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) est une instance entièrement gérée du moteur de base de données Microsoft SQL Server database qui fournit une compatibilité proche de 100% avec un serveur SQL sur place. Cette option prend en charge de plus grandes bases de données, jusqu’à 35 TB et est placé dans un [réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) pour un meilleur isolement.

- [Azure SQL Database serverless](https://docs.microsoft.com/azure/sql-database/sql-database-serverless) est un niveau de calcul pour une base de données unique qui évolue automatiquement en fonction de la demande de charge de travail. Il ne facture que pour le montant de calcul utilisé par seconde. Le service est bien adapté aux charges de travail avec des habitudes d’utilisation intermittentes et imprévisibles, entrecoupées de périodes d’inactivité. Le niveau de calcul sans serveur met également automatiquement en pause les bases de données pendant les périodes inactives afin que seules les charges de stockage soient facturées. Il reprend automatiquement lorsque l’activité revient.

Au-delà de la pile Microsoft SQL Server traditionnelle, Azure dispose également de versions gérées de trois bases de données open-source populaires.

## <a name="open-source-databases-in-azure"></a>Bases de données open-source en Azure

Les bases de données relationnelles open-source sont devenues un choix populaire pour les applications cloud-natives. Beaucoup d’entreprises les favorisent par rapport aux produits de base de données commerciaux, en particulier pour les économies de coûts. De nombreuses équipes de développement bénéficient de leur flexibilité, d’un développement soutenu par la communauté et d’un écosystème d’outils et d’extensions. Les bases de données open-source peuvent être déployées sur plusieurs fournisseurs de cloud, ce qui contribue à minimiser les préoccupations liées au « verrouillage des fournisseurs ».

Les développeurs peuvent facilement héberger n’importe quelle base de données open-source sur un Azure VM. Tout en assurant un contrôle total, cette approche vous met sur le crochet pour la gestion, la surveillance et la maintenance de la base de données et VM.

Cependant, Microsoft poursuit son engagement à maintenir Azure une «plate-forme ouverte» en offrant plusieurs bases de données open-source populaires en tant que services DBaaS *entièrement gérés.*

### <a name="azure-database-for-mysql"></a>Azure Database pour MySQL

[MySQL](https://en.wikipedia.org/wiki/MySQL) est une base de données relationnelle open-source et un pilier pour les applications construites sur la [pile logicielle LAMP](https://en.wikipedia.org/wiki/LAMP_(software_bundle)). Largement choisi pour lire les charges de travail *lourdes,* il est utilisé par de nombreuses grandes organisations, y compris Facebook, Twitter, et YouTube. L’édition communautaire est disponible gratuitement, tandis que l’édition d’entreprise nécessite un achat de licence. Créé à l’origine en 1995, le produit a été acheté par Sun Microsystems en 2008. Oracle a acquis Sun et MySQL en 2010.

[Azure Database pour MySQL](https://azure.microsoft.com/services/mysql/) est un service de base de données relationnelle géré basé sur le moteur Open source MySQL Server. Il utilise l’édition communautaire MySQL. Le serveur Azure MySQL est le point administratif du service. C’est le même moteur serveur MySQL utilisé pour les déploiements sur place. Le moteur peut créer une base de données unique par serveur ou plusieurs bases de données par serveur qui partagent des ressources. Vous pouvez continuer à gérer les données à l’aide des mêmes outils open-source sans avoir à acquérir de nouvelles compétences ou à gérer des machines virtuelles.

### <a name="azure-database-for-mariadb"></a>Azure Database for MariaDB

[MariaDB](https://mariadb.com/) Server est un autre serveur de base de données open-source populaire. Il a été créé comme une *fourchette* de MySQL quand Oracle a acheté Sun Microsystems, qui possédait MySQL. L’intention était de s’assurer que MariaDB restait open-source. Comme MariaDB est une fourche de MySQL, les définitions de données et de tables sont compatibles, et les protocoles, structures et API des clients sont étroitement liés.

MariaDB a une communauté forte et est utilisé par de nombreuses grandes entreprises. Alors qu’Oracle continue de maintenir, d’améliorer et de soutenir MySQL, la fondation MariaDB gère MariaDB, permettant aux contributions publiques au produit et à la documentation.

[Azure Database pour MariaDB](https://azure.microsoft.com/services/mariadb/) est une base de données relationnelle entièrement gérée en tant que service dans le cloud Azure. Le service est basé sur le moteur serveur d’édition communautaire MariaDB. Il peut gérer les charges de travail essentielles à la mission avec des performances prévisibles et une évolutivité dynamique.

### <a name="azure-database-for-postgresql"></a>Azure Database pour PostgreSQL

[PostgreSQL](https://www.postgresql.org/) est une base de données relationnelle open-source avec plus de 30 ans de développement actif. PostgresSQL a une solide réputation de fiabilité et d’intégrité des données. Il est riche en fonction, SQL conforme, et considéré comme plus performant que MySQL - en particulier pour les charges de travail avec des requêtes complexes et des écritures lourdes. De nombreuses grandes entreprises, dont Apple, Red Hat et Fujitsu, ont construit des produits à l’aide de PostgreSQL.

[Azure Database for PostgreSQL](https://azure.microsoft.com/services/postgresql/) est un service de base de données relationnel entièrement géré, basé sur le moteur de base de données Postgres open source. Le service prend en charge de nombreuses plates-formes de\#développement, y compris C , Java, Python, Node, C , et PHP. Vous pouvez y migrer les bases de données PostgreSQL à l’aide de l’outil [d’interface de ligne de commande](https://datamigration.microsoft.com/scenario/postgresql-to-azurepostgresql?step=1) ou du service de migration de données Azure.

La base de données Azure pour PostgreSQL est disponible avec deux options de déploiement :

- [L’option de](https://docs.microsoft.com/azure/postgresql/concepts-servers) déploiement Single Server est un point administratif central pour plusieurs bases de données auxquelles vous pouvez déployer de nombreuses bases de données. Le prix est structuré par serveur en fonction des cœurs et du stockage.

- [L’option Hyperscale (Citus)](https://azure.microsoft.com/blog/get-high-performance-scaling-for-your-azure-database-workloads-with-hyperscale/) est alimentée par la technologie Citus Data. Il permet des performances élevées *en évoluant horizontalement* une base de données unique sur des centaines de nœuds pour offrir des performances et une échelle rapides. Cette option permet au moteur d’adapter plus de données dans la mémoire, de faire la parallélisation des requêtes sur des centaines de nœuds et d’indexer plus rapidement les données.

## <a name="nosql-data-in-azure"></a>Données NoSQL en Azure

Cosmos DB est un service de base de données NoSQL entièrement géré et distribué dans le monde entier dans le cloud Azure. Il a été adopté par de nombreuses grandes entreprises à travers le monde, y compris Coca-Cola, Skype, ExxonMobil et Liberty Mutual.

Si vos services nécessitent une réponse rapide de n’importe où dans le monde, une grande disponibilité ou une évolutivité élastique, Cosmos DB est un excellent choix. Figure 5-12 montre Cosmos DB.

![Vue d’ensemble de Cosmos DB](./media/cosmos-db-overview.png)

**Figure 5-12**: Aperçu du Cosmos DB

Le chiffre précédent présente de nombreuses capacités intégrées en nuage-native disponibles dans Cosmos DB. Dans cette section, nous allons les examiner de plus près.

### <a name="global-support"></a>Support global

Les applications cloud-natives ont souvent un public mondial et nécessitent une échelle mondiale.

Vous pouvez distribuer des bases de données Cosmos dans toutes les régions ou dans le monde, en plaçant des données près de vos utilisateurs, en améliorant le temps de réponse et en réduisant la latence. Vous pouvez ajouter ou supprimer une base de données d’une région sans faire une pause ou redéployer vos services. En arrière-plan, Cosmos DB reproduit les données de manière transparente à chacune des régions configurées.

Cosmos DB prend en charge le clustering [actif/actif](https://kemptechnologies.com/white-papers/unfog-confusion-active-passive-activeactive-load-balancing/) au niveau mondial, vous permettant de configurer l’une de vos régions de base de données pour prendre en charge *les écrits et les lectures.*

Le protocole [Multi-Master](https://docs.microsoft.com/azure/cosmos-db/multi-master-benefits) est une caractéristique importante dans Cosmos DB qui permet la fonctionnalité suivante :

- Bénéficier d’une évolutivité élastique illimitée en écriture et en lecture.

- Disponibilité en lecture et en écriture de 99,999 % dans le monde entier.

- Lectures et écritures traitées en moins de 10 millisecondes au 99e centile.

Avec les API Cosmos DB [Multi-Homing,](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)votre microservice est automatiquement au courant de la région Azure la plus proche et lui envoie des demandes. La région la plus proche est identifiée par Cosmos DB sans aucun changement de configuration. Si une région devient indisponible, la fonction Multi-Homing acheminera automatiquement les demandes vers la région disponible la plus proche.

### <a name="multi-model-support"></a>Soutien multi-modèles

Lors de la réplatformation des applications monolithiques vers une architecture cloud-native, les équipes de développement doivent parfois migrer open-source, NoSQL data stores. Cosmos DB peut vous aider à préserver votre investissement dans ces datastores NoSQL grâce à sa plateforme de données *multi-modèles.* La figure 5-13 montre les API de [compatibilité](https://www.wikiwand.com/en/Cosmos_DB)NoSQL prises en charge .

![Fournisseurs Cosmos DB](./media/cosmos-db-providers.png)

**Figure 5-13**: Fournisseurs cosmos DB

Les équipes de développement peuvent migrer les bases de données existantes de Mongo, Gremlin ou Cassandra dans les bases de données Cosmos DB avec un minimum de modifications aux données ou au code. Pour les nouvelles applications, les équipes de développement peuvent choisir parmi les options open-source ou le modèle D’API SQL intégré.

> En interne, Cosmos stocke les données dans un format simple de struct composé de types de données primitives. Pour chaque demande, le moteur de base de données traduit les données primitives dans la représentation du modèle que vous avez sélectionnée.

Dans le chiffre précédent, 5-13, notez l’option [API de table.](https://docs.microsoft.com/azure/cosmos-db/table-introduction) Cette API est une évolution du stockage de table Azure. Les deux partagent le même modèle de table sous-jacent, mais l’API de table Cosmos DB ajoute des améliorations premium non disponibles dans l’API de stockage Azure. Ces caractéristiques sont contrastées dans la figure 5-4.

![API Table Azure](media/azure-table-api.png)

**Figure 5-14**: Fournisseurs d’API de table Azure

Les microservices qui consomment le stockage de la table Azure peuvent facilement migrer vers l’API de la table Cosmos DB. Le code n’a pas besoin d’être modifié.

### <a name="tunable-consistency"></a>Consistance de thon

Plus tôt dans la section *Relationnel vs NoSQL,* nous avons discuté de la cohérence des *données.* La cohérence des données fait référence à *l’intégrité* de vos données. Les services cloud-autochtones avec des données distribuées reposent sur la réplication et doivent faire un compromis fondamental entre la cohérence de lecture, la disponibilité et la latence.

La plupart des bases de données distribuées permettent aux développeurs de choisir entre deux modèles de cohérence : une forte cohérence et une cohérence éventuelle. *La forte cohérence* est l’étalon-or de la programmabilité des données. Il garantit qu’une requête retournera toujours les données les plus récentes - même si le système doit engager la latence en attendant qu’une mise à jour se reproduise sur toutes les copies de base de données. Bien qu’une base de données configurée pour *une éventuelle cohérence* renvoie immédiatement les données, même si ces données ne sont pas la copie la plus actuelle. Cette dernière option permet une plus grande disponibilité, une plus grande échelle et des performances accrues.

Azure Cosmos DB propose cinq modèles de [cohérence](https://docs.microsoft.com/azure/cosmos-db/consistency-levels) bien définis indiqués dans la figure 5-15.

![Graphique de cohérence Cosmos DB](./media/cosmos-consistency-level-graph.png)

**Figure 5-15**: Niveaux de cohérence Cosmos DB

 Ces options vous permettent de faire des choix précis et des compromis granulaires pour la cohérence, la disponibilité et les performances de vos données. La figure 5-16 décrit chaque niveau.

![Niveaux de cohérence Cosmos DB](./media/cosmos-db-consistency-levels.png)

**Figure 5-16**: Description du niveau de cohérence Cosmos DB

Dans l’article [Getting Behind the 9-Ball: Cosmos DB Consistency Levels Explained](https://blog.jeremylikness.com/blog/2018-03-23_getting-behind-the-9ball-cosmosdb-consistency-levels/), Microsoft Cloud Developer Advocate Jeremy Likeness fournit une excellente explication des cinq modèles.

### <a name="partitioning"></a>Partitionnement

Azure Cosmos DB adopte [le partitionnement](https://docs.microsoft.com/azure/cosmos-db/partitioning-overview) automatique pour mettre à l’échelle une base de données pour répondre aux besoins de performance de vos services cloud-native.

Vous gérez les données dans les données Cosmos DB en créant des bases de données, des conteneurs et des éléments.

Les conteneurs vivent dans une base de données Cosmos DB et représentent un groupement schéma-agnostique d’éléments. Les éléments sont les données que vous ajoutez au conteneur. Ils sont représentés comme des documents, des rangées, des nœuds ou des bords. Tous les éléments ajoutés à un conteneur sont automatiquement indexés.

Pour diviser le conteneur, les articles sont divisés en sous-ensembles distincts appelés cloisons logiques. Les cloisons logiques sont peuplées en fonction de la valeur d’une clé de partition associée à chaque élément d’un conteneur. La figure 5-18 montre deux conteneurs chacun avec une partition logique basée sur une valeur clé de partition.

![Mécanique de partitionnement Cosmos DB](./media/cosmos-db-partitioning.png)

**Figure 5-18**: Mécanique de partitionnage Cosmos DB

Notez dans le chiffre précédent comment chaque élément inclut une clé de partition de « ville » ou d'« aéroport ». La clé détermine la partition logique de l’élément. Les articles munis d’un code de la ville sont attribués au conteneur à gauche, et aux articles avec un code d’aéroport, au conteneur de droite. La combinaison de la valeur de clé de partition avec la valeur d’identification crée l’index d’un élément, qui identifie uniquement l’élément.

En interne, Cosmos DB gère automatiquement le placement de [cloisons logiques](https://docs.microsoft.com/azure/cosmos-db/partition-data) sur les cloisons physiques pour satisfaire les besoins d’évolutivité et de performance du conteneur. À mesure que les exigences en matière de débit d’application et de stockage augmentent, Azure Cosmos DB redistribue les partitions logiques sur un plus grand nombre de serveurs. Les opérations de redistribution sont gérées par Cosmos DB et invoquées sans interruption ni temps d’arrêt.

## <a name="newsql-databases"></a>Bases de données NewSQL

*NewSQL* est une nouvelle technologie de base de données qui combine l’évolutivité distribuée de NoSQL avec les garanties ACID d’une base de données relationnelle. Les bases de données NewSQL sont importantes pour les systèmes d’entreprise qui doivent traiter des volumes élevés de données, dans des environnements distribués, avec un soutien transactionnel complet et la conformité ACID. Bien qu’une base de données NoSQL puisse fournir une évolutivité massive, elle ne garantit pas la cohérence des données. Les problèmes intermittents liés à des données incohérentes peuvent imposer un fardeau à l’équipe de développement. Les développeurs doivent construire des garanties dans leur code de microservice pour gérer les problèmes causés par des données incohérentes.

La Cloud Native Computing Foundation (CNCF) présente plusieurs projets de base de données NewSQL.

| Projet | Caractéristiques |
| :-------- | :-------- |
| Cafard DB |Une base de données relationnelle conforme à l’ACID qui s’échelle à l’échelle mondiale. Ajoutez un nouveau nœud à un cluster et CockroachDB s’occupe d’équilibrer les données entre les instances et les zones géographiques. Il crée, gère et distribue des répliques pour assurer la fiabilité. Il est open source et disponible gratuitement.  |
| TiDB (TiDB) | Une base de données open-source qui prend en charge les charges de travail hybrides de traitement transactionnel et analytique (HTAP). Il est compatible MySQL et dispose d’une évolutivité horizontale, d’une forte cohérence et d’une grande disponibilité.  TiDB agit comme un serveur MySQL. Vous pouvez continuer à utiliser les bibliothèques de clients MySQL existantes, sans nécessiter de modifications importantes du code de votre application. |
| YugabyteDB | Une base de données SQL open source, performante et distribuée. Il soutient une faible latence des requêtes, une résilience contre les échecs et une distribution mondiale de données. YugabyteDB est compatible PostgressSQL et gère les charges de travail RDBMS et l’OLTP à l’échelle Internet. Le produit supporte également NoSQL et est compatible avec Cassandra. |
|Vitess Vitess | Vitess est une solution de base de données pour le déploiement, la mise à l’échelle et la gestion de grands groupes d’instances MySQL. Il peut fonctionner dans une architecture cloud publique ou privée. Il combine et étend de nombreuses caractéristiques importantes MySQL et dispose à la fois verticale et horizontale support d’éclat. Originaire de YouTube, Vitess dessert tous les trafics de bases de données YouTube depuis 2011. |

Les projets open-source du chiffre précédent sont disponibles auprès de la Cloud Native Computing Foundation. Trois des offres sont des produits de base de données complets, qui comprennent le support .NET Core. L’autre, Vitess, est un système de clustering de base de données qui échelle horizontalement de grands groupes d’instances MySQL.

L’un des principaux objectifs de conception des bases de données NewSQL est de travailler nativement à Kubernetes, en profitant de la résilience et de l’évolutivité de la plate-forme.

Les bases de données NewSQL sont conçues pour prospérer dans des environnements cloud éphémères où les machines virtuelles sous-jacentes peuvent être redémarrées ou reprogrammées à tout moment. Les bases de données sont conçues pour survivre aux défaillances de nœuds sans perte de données ni temps d’arrêt. CockroachDB, par exemple, est capable de survivre à une perte de machine en maintenant trois répliques cohérentes de toutes les données à travers les nœuds dans un cluster.

Kubernetes utilise une *construction Services* pour permettre à un client de s’adresser à un groupe de processus identiques de bases de données NewSQL à partir d’une seule entrée DNS. En découplant les instances de base de données à partir de l’adresse du service auquel elle est associée, nous pouvons évoluer sans perturber les instances d’application existantes. L’envoi d’une demande à n’importe quel service à un moment donné donnera toujours le même résultat.

Dans ce scénario, tous les cas de base de données sont égaux. Il n’y a pas de relations primaires ou secondaires. Des techniques comme *la réplication consensuelle* trouvée dans CockroachDB permettent à n’importe quel nœud de base de données de traiter n’importe quelle demande. Si le nœud qui reçoit une demande équilibrée de charge a les données dont il a besoin localement, il répond immédiatement. Si ce n’est pas le cas, le nœud devient une passerelle et transmet la demande aux nœuds appropriés pour obtenir la bonne réponse. Du point de vue du client, chaque nœud de base de données est le même : ils apparaissent comme une base de données *logique* unique avec les garanties de cohérence d’un système monopi machine, bien qu’il ait des dizaines, voire des centaines de nœuds qui travaillent dans les coulisses.

Pour un aperçu détaillé de la mécanique derrière les bases de données NewSQL, consultez [l’article DASH: Four Properties of Kubernetes-Native Databases.](https://thenewstack.io/dash-four-properties-of-kubernetes-native-databases/)

## <a name="data-migration-to-the-cloud"></a>Migration de données vers le cloud

L’une des tâches les plus longues est la migration des données d’une plate-forme de données à l’autre. Le [service de migration de données Azure](https://azure.microsoft.com/services/database-migration/) peut aider à accélérer ces efforts. Il peut migrer des données de plusieurs sources de bases de données externes vers les plates-formes Azure Data avec un temps d’arrêt minimal. Les plates-formes cibles comprennent les services suivants :

- Azure SQL Database
- Azure Database pour MySQL
- Azure Database for MariaDB
- Azure Database pour PostgreSQL
- CosmosDB
  
Le service fournit des recommandations pour vous guider à travers les changements nécessaires pour exécuter une migration, petites ou grandes.

>[!div class="step-by-step"]
>[Suivant précédent](database-per-microservice.md)
>[Next](azure-caching.md)
