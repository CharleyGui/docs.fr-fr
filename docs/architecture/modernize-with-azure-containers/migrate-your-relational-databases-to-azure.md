---
title: Migrez vos bases de données relationnelles en azur
description: Moderniser les applications .NET existantes avec le cloud Azure et les conteneurs Windows (fr) migrer vos bases de données relationnelles en azur
ms.date: 04/28/2018
ms.openlocfilehash: efd1548c3f74fc27450f4949d71a1c4d61907ba5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093614"
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrez vos bases de données relationnelles en azur

Vision : Azure offre la migration de base de données la plus complète.

Dans Azure, vous pouvez migrer vos serveurs de base de données directement vers les VM IaaS (pure ascenseur et décalage), ou vous pouvez migrer vers la base de données SqL Azure, pour des avantages supplémentaires. Azure SQL Database propose des options d’instance gérée et de base de données complète en tant que service (DBaaS). La figure 3-1 montre les multiples trajectoires de migration relationnelles disponibles à Azure.

![Chemins de migration de base de données à Azure](./media/image3-1.png)

**Figure 3-1.** Chemins de migration de base de données à Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Quand migrer vers Azure SQL Base de données Instance gérée

Dans la plupart des cas, Azure SQL Database Managed Instance sera votre meilleure option à considérer lorsque vous migrez vos données vers Azure. Si vous migrez dans les bases de données SQL Server et que vous avez besoin de près de 100 % d’assurance que vous n’aurez pas besoin de réécolitiser votre application ou d’apporter des modifications à votre code d’accès aux données ou à vos données, choisissez la fonction d’instance gérée de la base de données SqL Azure.

Azure SQL Database Managed Instance est la meilleure option si vous avez des exigences supplémentaires pour les fonctionnalités de niveau d’instance SQL Server, ou des exigences d’isolement au-delà des fonctionnalités fournies dans une base de données Azure SQL standard (modèle de base de données unique). Ce dernier est le choix le plus orienté paaS, mais il n’offre pas les mêmes fonctionnalités que celle d’un serveur SQL traditionnel. La migration peut faire surface.

Par exemple, une organisation qui a fait des investissements importants dans les capacités SQL Server de niveau exemple gagnerait à migrer vers SQL Managed Instance. Parmi les exemples de capacités SQL Server au niveau de l’instance, mentionnons l’intégration de l’heure d’exécution de langage courant (CLR) de SQL, l’agent serveur SQL et les requêtes transversales. La prise en charge de ces fonctionnalités n’est pas disponible dans la base de données Standard Azure SQL (un modèle de base de données unique).

Une organisation qui exerce ses activités dans une industrie très réglementée et qui doit maintenir l’isolement à des fins de sécurité pourrait également tirer avantager le choix du modèle SQL Managed Instance.

L’instance gérée dans la base de données Azure SQL a les caractéristiques suivantes :

- Isolement de sécurité via Azure Virtual Network

- Compatibilité de surface d’application, avec ces caractéristiques :

  - SQL Server Agent et SQL Server Profiler

  - Références et requêtes transversales, SQL CLR, réplication, saisie de données de modification (CDC) et Courtier en services

- Taille des bases de données jusqu’à 35 TB

- Migration de temps d’arrêt minimum, avec ces caractéristiques :

  - Azure Database Migration Service

  - Sauvegarde et restauration indigènes, et expédition de journal

Avec ces fonctionnalités, lorsque vous migrez les bases de données d’applications existantes vers la base de données d’Azure SQL, le modèle d’instance gérée offre près de 100% des avantages de PaaS pour SQL Server. Managed Instance est un environnement SQL Server où vous continuez à utiliser des capacités de niveau d’instance sans modifier votre conception d’application.

Managed Instance est probablement le meilleur ajustement pour les entreprises qui utilisent actuellement SQL Server, et qui nécessitent une flexibilité dans leur sécurité réseau dans le cloud. C’est comme avoir un réseau virtuel privé pour vos bases de données SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Quand migrer vers la base de données SqL Azure

Comme mentionné, la base de données Standard Azure SQL est un DBaaS entièrement géré et relationnel. SQL Database gère actuellement des millions de bases de données de production, réparties dans 38 centres de données, à travers le monde. Il prend en charge un large éventail d’applications et de charges de travail, allant de la gestion de données transactionnelles simples à la conduite des applications les plus exigeantes en données et essentielles à la mission qui nécessitent un traitement avancé des données à l’échelle mondiale.

En raison de ses fonctionnalités PaaS complètes, de meilleurs prix - et finalement un coût inférieur - vous devriez passer à la base de données Standard Azure SQL comme votre «choix par défaut» si vous avez une application qui utilise de base, bases de données SQL standard, et aucune fonctionnalité d’instance supplémentaire. Les fonctionnalités SQL Server comme l’intégration SQL CLR, SQL Server Agent et les requêtes transversales ne sont pas prises en charge dans la base de données Standard Azure SQL. Ces fonctionnalités ne sont disponibles que dans le modèle Azure SQL Database Managed Instance.

Azure SQL Database est le seul service intelligent de base de données cloud conçu pour les développeurs d’applications. C’est aussi le seul service de base de données cloud qui s’évolue à la volée, sans temps d’arrêt, pour vous aider à fournir efficacement des applications multitenants. En fin de compte, Azure SQL Database vous laisse plus de temps pour innover, et il accélère votre temps de mise sur le marché. Vous pouvez créer des applications sécurisées et vous connecter à votre base de données SQL en utilisant les langues et les plates-formes que vous préférez.

Azure SQL Database offre les avantages suivants :

- Intelligence intégrée (apprentissage automatique) qui apprend et s’adapte à votre application

- Fourniture de bases de données à la demande

- Une gamme d’offres, pour toutes les charges de travail

- 99,99% disponibilité SLA, zéro entretien

- Géoréfélication et restauration des services de protection des données

- Azure SQL Database Point in Time Restore fonctionnalité

- Compatibilité avec SQL Server 2016, y compris l’hybride et la migration

La base de données Standard Azure SQL est plus proche de PaaS que l’instance gérée par la base de données SQL Azure. Préférez la base de données Standard Azure SQL car vous bénéficierez de plus d’avantages d’un cloud géré. Cependant, Azure SQL Database présente certaines différences clés par rapport aux instances régulières et sur site SQL Server. Selon les exigences de votre application actuelle en matière de base de données et les exigences et politiques de votre entreprise, ce n’est peut-être pas le meilleur choix lorsque vous planifiez votre migration vers le cloud.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Quand déplacer votre RDBMS d’origine à un VM (IaaS)

Une de vos options de migration est de déplacer votre système de gestion de base de données relationnelle d’origine (RDBMS), y compris Oracle, IBM DB2, MySQL, PostgreSQL, ou SQL Server, à un serveur similaire qui fonctionne sur un Azure VM. Si vous avez des applications existantes qui nécessitent la migration la plus rapide vers le cloud avec un minimum de modifications, ou pas de changements du tout, une migration directe vers IaaS dans le cloud pourrait être une option équitable. Ce n’est peut-être pas la meilleure façon de profiter de tous les avantages du cloud, mais c’est probablement le chemin initial le plus rapide.

Actuellement, Microsoft Azure prend en charge jusqu’à [331 serveurs de base de données différents](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) déployés sous forme de VM IaaS. Il s’agit notamment de RDBMS populaires comme SQL Server, Oracle, MySQL, PostgreSQL, et IBM DB2, et de nombreuses autres bases de données NoSQL comme MongoDB, Cassandra, DataStax, MariaDB, et Cloudera.

> [!NOTE]
> Bien que le déplacement de votre RDBMS vers une VM Azure puisse être le moyen le plus rapide de migrer vos données vers le cloud (parce qu’il s’agit d’IaaS), cette approche nécessite un investissement important dans vos équipes informatiques (administrateurs de bases de données et professionnels de l’informatique). Les équipes d’entreprise doivent être en mesure de mettre en place et de gérer la haute disponibilité, la récupération en cas de catastrophe et le patching pour SQL Server. Ce contexte a également besoin d’un environnement personnalisé, avec des droits administratifs complets.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Quand migrer vers SQL Server en tant que VM (IaaS)

Il pourrait y avoir quelques cas où vous avez encore besoin de migrer vers SQL Server comme un VM régulier. Un exemple de scénario est si vous avez besoin d’utiliser SQL Server Reporting Services. Dans la plupart des cas, cependant, Azure SQL Database Managed Instance peut fournir tout ce dont vous avez besoin pour migrer à partir de serveurs SQL sur place, de sorte que la migration vers un serveur SQL VM devrait être votre dernier recours à essayer.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Utilisez azure Database Migration Service pour migrer vos bases de données relationnelles vers Azure

Vous pouvez utiliser Azure Database Migration Service pour migrer des bases de données relationnelles comme SQL Server, Oracle et MySQL vers Azure, que votre base de données cible soit Azure SQL Database, Azure SQL Database Managed Instance ou SQL Server sur un Azure VM.

Le flux de travail automatisé, avec les rapports d’évaluation, vous guide à travers les modifications que vous devez apporter avant de migrer la base de données. Lorsque vous êtes prêt, le service migre la base de données source vers Azure.

Chaque fois que vous modifiez un RDBMS original, vous devrez peut-être retester. Vous devrez peut-être également modifier les phrases SQL ou le code de cartographie relationnelle (ORM) dans votre application, selon les résultats des tests.

Si vous avez une autre base de données (par exemple, IBM DB2) et que vous optez pour une approche de levage et de changement, vous voudrez peut-être continuer à utiliser ces bases de données sous forme de VM IaaS à Azure, à moins que vous ne soyez prêt à effectuer une migration de données plus complexe. Une migration de données plus complexe nécessitera des efforts supplémentaires parce que vous migreriez vers un type de base de données différent avec de nouveaux schémas et différentes bibliothèques de programmation.

Pour savoir comment migrer les bases de données en utilisant azure Database Migration Service, consultez [le cloud plus rapidement avec Azure SQL Database Managed Instance et Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Ressources supplémentaires

- **Choisissez une option de serveur SQL cloud : Azure SQL Database (PaaS) ou SQL Server sur Azure VM (IaaS)**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **Rendez-vous plus rapidement sur le cloud grâce à Azure SQL DB Managed Instance and Database Migration Service**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **Migration de base de données SQL Server vers SQL Database dans le cloud**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Azure SQL Database**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **Serveur SQL sur les machines virtuelles**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [Suivant précédent](lift-and-shift-existing-apps-azure-iaas.md)
> [Next](modernize-existing-apps-to-cloud-optimized/index.md) <!-- Next Chapter -->
