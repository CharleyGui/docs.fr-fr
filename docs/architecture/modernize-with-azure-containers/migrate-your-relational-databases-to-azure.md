---
title: Migrer vos bases de données relationnelles vers Azure
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | migrer vos bases de données relationnelles vers Azure
ms.date: 12/21/2020
ms.openlocfilehash: c8dc92e1c5c5fb36a68bcad000c10e47c946ca0c
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025379"
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrer vos bases de données relationnelles vers Azure

Vision : Azure offre la migration de base de données la plus complète.

Dans Azure, vous pouvez migrer vos serveurs de base de données directement vers des machines virtuelles IaaS (élévation et déplacement purs), ou vous pouvez migrer vers Azure SQL Database, pour bénéficier d’avantages supplémentaires. Azure SQL Database offre les options instance gérée et base de données en tant que service (DBaaS) complète. La figure 3-1 montre les différents chemins de migration de base de données relationnelle disponibles dans Azure.

![Chemins de migration de base de données dans Azure](./media/image3-1.png)

**Figure 3-1.** Chemins de migration de base de données dans Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Quand migrer vers Azure SQL Database Managed Instance

Dans la plupart des cas, Azure SQL Database Managed Instance constitue la meilleure option à prendre en compte lorsque vous migrez vos données vers Azure. Si vous migrez des bases de données SQL Server et que vous avez besoin de près de 100% d’assurance que vous n’avez pas besoin de remanier votre application ou d’apporter des modifications à vos données ou code d’accès aux données, choisissez la fonctionnalité Managed Instance de Azure SQL Database.

Azure SQL Database Managed Instance est la meilleure option si vous avez des exigences supplémentaires pour SQL Server des fonctionnalités au niveau de l’instance ou des exigences d’isolation au-delà des fonctionnalités fournies dans un Azure SQL Database standard (modèle de base de données unique). Ce dernier est le choix le plus axé sur le PaaS, mais il n’offre pas les mêmes fonctionnalités que celles d’un serveur SQL traditionnel. La migration peut faire face aux frottements.

Par exemple, une organisation qui a fait des investissements approfondis dans les fonctionnalités de SQL Server au niveau de l’instance peut tirer parti de la migration vers SQL Managed Instance. Parmi les exemples de fonctionnalités de SQL Server au niveau de l’instance, citons l’intégration de SQL common language runtime (CLR), SQL Server Agent et l’interrogation de bases de données croisées. La prise en charge de ces fonctionnalités n’est pas disponible dans les Azure SQL Database standard (modèle à base de données unique).

Une organisation qui opère dans un secteur hautement réglementé et qui doit maintenir l’isolation pour des raisons de sécurité, peut également tirer parti du choix du modèle SQL Managed Instance.

Managed Instance dans Azure SQL Database présente les caractéristiques suivantes :

- Isolation de la sécurité via le réseau virtuel Azure

- Compatibilité avec les fonctionnalités de l’application, avec les fonctionnalités suivantes :

  - SQL Server Agent et SQL Server Profiler

  - Références et requêtes de bases de données croisées, CLR SQL, réplication, capture de données modifiées (CDC) et Service Broker

- Taille de la base de données jusqu’à 35 to

- Migration minimale des temps d’arrêt, avec les fonctionnalités suivantes :

  - Azure Database Migration Service

  - Sauvegarde et restauration natives et copie des journaux de session

Grâce à ces fonctionnalités, lorsque vous migrez des bases de données d’application existantes vers Azure SQL Database, le modèle de Managed Instance offre près de 100% des avantages de PaaS pour SQL Server. Managed Instance est un environnement SQL Server dans lequel vous continuez à utiliser des fonctionnalités au niveau de l’instance sans modifier la conception de votre application.

Managed Instance est probablement la meilleure solution pour les entreprises qui utilisent actuellement des SQL Server et qui nécessitent de la flexibilité dans la sécurité de leur réseau dans le Cloud. C’est comme s’il s’agissait d’un réseau virtuel privé pour vos bases de données SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Quand migrer vers Azure SQL Database

Comme nous l’avons vu, le Azure SQL Database standard est un DBaaS relationnel entièrement géré. SQL Database gère actuellement des millions de bases de données de production, dans des centres de données de 38, dans le monde entier. Il prend en charge un large éventail d’applications et de charges de travail, de la gestion des données transactionnelles directes, à la mise en œuvre des applications stratégiques les plus gourmandes en données nécessitant un traitement de données avancé à l’échelle mondiale.

En raison de ses fonctionnalités PaaS complètes, d’une meilleure tarification et d’un coût réduit, vous devez passer au Azure SQL Database standard comme votre choix par défaut si vous avez une application qui utilise des bases de données SQL de base, standard et aucune autre fonctionnalité d’instance. Les fonctionnalités de SQL Server telles que l’intégration du CLR SQL, les SQL Server Agent et l’interrogation des bases de données croisées ne sont pas prises en charge dans le Azure SQL Database standard. Ces fonctionnalités sont disponibles uniquement dans le modèle de Azure SQL Database Managed Instance.

Azure SQL Database est le seul service de base de données Cloud intelligent conçu pour les développeurs d’applications. C’est également le seul service de base de données Cloud qui évolue à la volée, sans temps d’arrêt, pour vous aider à fournir efficacement des applications mutualisées. Au final, Azure SQL Database vous laisse plus de temps pour innover et accélère votre délai de commercialisation. Vous pouvez créer des applications sécurisées et vous connecter à votre base de données SQL à l’aide des langages et des plateformes que vous préférez.

Azure SQL Database offre les avantages suivants :

- Intelligence intégrée (Machine Learning) qui apprend et s’adapte à votre application

- Configuration de base de données à la demande

- Une gamme d’offres, pour toutes les charges de travail

- contrat SLA de disponibilité 99,99%, maintenance nulle

- Services de géo-réplication et de restauration pour la protection des données

- Azure SQL Database fonctionnalité de restauration dans le temps

- Compatibilité avec SQL Server 2016, y compris l’Hybrid et la migration

La Azure SQL Database standard est plus proche de PaaS que Azure SQL Database Managed Instance. Préférez le Azure SQL Database standard, car vous obtiendrez plus d’avantages d’un Cloud géré. Toutefois, Azure SQL Database présente certaines différences clés par rapport aux instances de SQL Server normales et locales. Selon les exigences de la base de données de votre application existante, ainsi que les exigences et stratégies de votre entreprise, il peut ne pas être le meilleur choix lorsque vous planifiez votre migration vers le Cloud.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Quand déplacer votre SGBDR d’origine vers une machine virtuelle (IaaS)

L’une de vos options de migration consiste à déplacer votre système de gestion de base de données relationnelle (SGBDR) d’origine, y compris Oracle, IBM DB2, MySQL, PostgreSQL ou SQL Server, vers un serveur similaire qui s’exécute sur une machine virtuelle Azure. Si vous avez des applications qui requièrent la migration la plus rapide vers le Cloud avec des modifications minimes, ou si aucune modification n’est apportée, une migration directe vers IaaS dans le Cloud peut être une bonne option. Il est possible qu’il ne s’agisse pas de la meilleure façon de tirer parti de tous les avantages du Cloud, mais c’est probablement le chemin initial le plus rapide.

Actuellement, Microsoft Azure prend en charge jusqu’à [331 serveurs de base de données différents](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) déployés en tant que machines virtuelles IaaS. Il s’agit notamment de SGBDR populaires comme SQL Server, Oracle, MySQL, PostgreSQL et IBM DB2, ainsi que de nombreuses autres bases de données NoSQL telles que MongoDB, Cassandra, DataStax, MariaDB et Cloudera.

> [!NOTE]
> Bien que le déplacement de votre SGBDR vers une machine virtuelle Azure puisse être le moyen le plus rapide de migrer vos données vers le Cloud (car il s’agit d’IaaS), cette approche nécessite un investissement significatif dans les équipes informatiques (administrateurs de base de données et professionnels de l’informatique). Les équipes d’entreprise doivent être en mesure de configurer et de gérer la haute disponibilité, la récupération d’urgence et l’application de correctifs pour SQL Server. Ce contexte a également besoin d’un environnement personnalisé, avec des droits d’administration complets.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Quand migrer vers SQL Server en tant que machine virtuelle (IaaS)

Il peut arriver que vous deviez migrer vers SQL Server en tant que machine virtuelle standard. C’est le cas, par exemple, si vous devez utiliser SQL Server Reporting Services. Toutefois, dans la plupart des cas, Azure SQL Database Managed Instance pouvez fournir tout ce dont vous avez besoin pour migrer à partir de serveurs SQL Server locaux. par conséquent, la migration vers une machine virtuelle SQL Server doit être votre dernier recours.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Utiliser Azure Database Migration Service pour migrer vos bases de données relationnelles vers Azure

Vous pouvez utiliser Azure Database Migration Service pour migrer des bases de données relationnelles comme SQL Server, Oracle et MySQL vers Azure, que votre base de données cible soit Azure SQL Database, Azure SQL Database Managed Instance ou SQL Server sur une machine virtuelle Azure.

Le flux de travail automatisé, avec la création de rapports d’évaluation, vous guide tout au long des modifications que vous devez effectuer avant de migrer la base de données. Lorsque vous êtes prêt, le service migre la base de données source vers Azure.

Chaque fois que vous modifiez un SGBDR d’origine, vous devrez peut-être retester. Vous devrez peut-être également modifier les phrases SQL ou le code de mappage d' Object-Relational (ORM) dans votre application, en fonction des résultats des tests.

Si vous disposez d’une autre base de données (par exemple, IBM DB2) et que vous optez pour une approche d’élévation et de décalage, vous pouvez continuer à utiliser ces bases de données en tant que machines virtuelles IaaS dans Azure, sauf si vous êtes disposé à effectuer une migration de données plus complexe. Une migration de données plus complexe nécessite des efforts supplémentaires, car vous migrez vers un type de base de données différent avec le nouveau schéma et des bibliothèques de programmation différentes.

Pour savoir comment migrer des bases de données à l’aide de Azure Database Migration Service, consultez [accéder au Cloud plus rapidement avec Azure SQL Database Managed instance et Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Ressources supplémentaires

- **Choisir une option Cloud SQL Server : Azure SQL Database (PaaS) ou SQL Server sur une machine virtuelle Azure (IaaS)**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **Accédez au Cloud plus rapidement avec Azure SQL DB Managed Instance et Database Migration Service**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **Migration de base de données SQL Server vers SQL Database dans le cloud**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Azure SQL Database**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **SQL Server sur les machines virtuelles**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [Précédent](lift-and-shift-existing-apps-azure-iaas.md) 
>  [Suivant](modernize-existing-apps-to-cloud-optimized/index.md) <!-- Next Chapter -->
