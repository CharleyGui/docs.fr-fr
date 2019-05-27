---
title: Migrer vos bases de données relationnelles vers azure
description: Moderniser des Applications .NET existantes avec le Cloud Azure et les conteneurs Windows | migrer vos bases de données relationnelles vers azure
ms.date: 04/28/2018
ms.openlocfilehash: 3d4f03e61144bb6a442a50916d7fd024d38ec611
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051922"
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrer vos bases de données relationnelles vers azure

Vision : Azure offre la migration la plus complète de la base de données.

Dans Azure, vous pouvez migrer vos serveurs de base de données directement vers les machines virtuelles IaaS (pure lift- and -shift), ou vous pouvez migrer vers Azure SQL Database, des avantages supplémentaires. Base de données SQL Azure offre d’instance gérée et options de complète base de données-as-a-service (DBaaS). Figure 3-1 indique la base de données relationnelle plusieurs chemins de migration disponibles dans Azure.

![Chemins de migration de base de données dans Azure](./media/image3-1.png)

> **Figure 3-1** : Chemins de migration de base de données dans Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Quand migrer vers Azure SQL Database Managed Instance

Dans la plupart des cas, Azure SQL Database Managed Instance sera votre meilleure option à prendre en compte lorsque vous migrez vos données vers Azure. Si vous migrez les bases de données SQL Server et que vous devez presque les assurance 100 % que vous ne devez remanier votre application ou d’apporter des modifications à vos données ou le code d’accès aux données, choisissez la fonctionnalité de Managed Instance de base de données SQL Azure.

Azure SQL Database Managed Instance est la meilleure option si vous avez des exigences supplémentaires pour les fonctionnalités de niveau d’instance de SQL Server ou aux exigences d’isolation au-delà des fonctionnalités fournies dans une base de données SQL Azure standard (modèle de base de données unique). Cette dernière est le choix plus orientée services PaaS, mais elle n’offre pas les mêmes fonctionnalités que celui de SQL server traditionnel. Migration peut se manifester frictions.

Par exemple, une organisation qui a investi approfondie dans les fonctionnalités de niveau de l’instance SQL Server bénéficient d’une migration vers SQL Managed Instance. Exemples de fonctionnalités de SQL Server au niveau de l’instance incluent SQL intégration common language runtime (CLR), SQL Server Agent et des bases de données croiséesent interrogation. Prise en charge de ces fonctionnalités n’est pas disponible dans Azure SQL Database standard (un modèle de base de données unique).

Une organisation qui fonctionne dans un secteur hautement réglementé, et qui doit garantir l’isolation pour des raisons de sécurité, peut-être également bénéficier de choisir le modèle SQL Managed Instance.

Instance gérée dans la base de données SQL Azure présente les caractéristiques suivantes :

- Isolation de sécurité via le réseau virtuel Azure

- Compatibilité d’aire de conception application, avec ces fonctionnalités :

  - L’Agent SQL Server et SQL Server Profiler

  - Réplication de références et les requêtes SQL CLR, des bases de données croisées, capture de données modifiées (CDC) et Service Broker

- Tailles de base de données jusqu'à 35 To

- Migration de temps d’arrêt minimum, avec ces fonctionnalités :

  - Azure Database Migration Service

  - Sauvegarde en mode natif et de restauration et de l’envoi de journaux

Avec ces fonctionnalités, lorsque vous migrez des bases de données application existantes vers Azure SQL Database, le modèle de Managed Instance offre presque 100 % des avantages de PaaS pour SQL Server. Managed Instance est un environnement de SQL Server où vous continuer à utiliser les fonctionnalités de niveau d’instance sans modifier la conception de votre application.

Instance managée est probablement la meilleure solution pour les entreprises qui en sont à l’aide de SQL Server, et pour lesquelles la flexibilité dans la sécurité réseau dans le cloud. Cela revient à avoir un réseau privé virtuel pour vos bases de données SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Quand migrer vers Azure SQL Database

Comme mentionné, la base de données SQL Azure standard est un DBaaS entièrement gérée et relationnelle. Base de données SQL gère actuellement des millions de bases de données de production, dans 38 centres de données, dans le monde entier. Il prend en charge un large éventail d’applications et charges de travail, de la gestion des données transactionnelles simples, à la direction des applications plus gourmandes en données, stratégiques qui nécessitent le traitement avancé des données à l’échelle mondiale.

En raison de ses fonctionnalités PaaS complètes, meilleurs tarifs- et finalement coût-vous devez déplacer la base de données SQL Azure standard comme « choix par défaut » si vous avez une application qui utilise base, standard SQL bases de données et aucune fonctionnalité d’instance supplémentaires. Fonctionnalités de SQL Server, comme l’intégration du CLR SQL, SQL Server Agent et l’interrogation de bases de données croisées ne sont pas pris en charge dans la base de données SQL Azure standard. Ces fonctionnalités sont disponibles uniquement dans le modèle Azure SQL Database Managed Instance.

Base de données SQL Azure est le service de base de données de cloud uniquement intelligent qui est conçu pour les développeurs d’applications. Il est également le seul service de base de données de cloud qui s’adapte à la volée, sans temps d’arrêt, pour vous aider à distribuer efficacement des applications multi-locataires. Finalement, base de données SQL Azure vous laisse plus de temps pour innover et il accélère la votre marché. Vous pouvez générer des applications sécurisées et se connecter à votre base de données SQL en utilisant les langages et plateformes que vous préférez.

Base de données SQL Azure offre les avantages suivants :

- Intelligence intégrée (apprentissage) qui apprend et s’adapte à votre application

- Approvisionnement de la base de données à la demande

- Offres spéciales, pour toutes les charges de travail

- disponibilité de 99,99 % SLA, sans maintenance

- Géo-réplication et restauration des services de protection des données

- Point de base de données SQL Azure dans la fonctionnalité Restauration du temps

- Compatibilité avec SQL Server 2016, y compris hybride et migration

La base de données SQL Azure standard est plus proche PaaS que Azure SQL Database Managed Instance. Préférez la base de données SQL Azure standard, car vous obtiendrez plus d’avantages à partir d’un cloud géré. Toutefois, Azure SQL Database présente des différences clés de normal et les instances de SQL Server sur site. En fonction des besoins de base de données de votre application existante et vos exigences d’entreprise et les stratégies, il ne peut pas être le meilleur choix lorsque vous planifiez votre migration vers le cloud.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Transfert de votre SGBDR d’origine à une machine virtuelle (IaaS)

Une de vos options de migration consiste à déplacer votre d’origine système de gestion de base de données relationnelle (SGBDR), notamment Oracle, IBM DB2, MySQL, PostgreSQL ou SQL Server, à un serveur similaire qui s’exécute sur une machine virtuelle Azure. Si vous avez des applications existantes qui requièrent la migration le plus rapide vers le cloud avec un minimum de modifications ou aucune modification du tout, une migration directe vers IaaS dans le cloud peut être une option de répartition de charge. Il peut ne pas être la meilleure façon de tirer parti des avantages de tous les du cloud, mais il est probablement le chemin d’accès initial plus rapide.

Actuellement, Microsoft Azure prend en charge jusqu'à [des serveurs de base de données différente 331](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) déployés en tant que machines virtuelles IaaS. Ceux-ci incluent un SGBDR populaires tels que SQL Server, Oracle, MySQL, PostgreSQL et IBM DB2 et plusieurs autres bases de données NoSQL comme MongoDB, Cassandra, DataStax, MariaDB et Cloudera.

> [!NOTE]
> Bien que le déplacement de votre SGBDR pour une machine virtuelle Azure peut être le moyen le plus rapide pour migrer vos données vers le cloud (car il IaaS), cette approche nécessite un investissement significatif dans vos équipes informatique (administrateurs de base de données et les professionnels de l’informatique). Équipes d’entreprise doivent être en mesure de configurer et gérer une haute disponibilité, la récupération d’urgence et la mise à jour corrective pour SQL Server. Ce contexte a également besoin d’un environnement personnalisé, avec les droits d’administration complets.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Quand migrer vers SQL Server comme une machine virtuelle (IaaS)

Il existe peut-être quelques cas où vous devez toujours effectuer la migration vers SQL Server comme une machine virtuelle standard. Un exemple de scénario est si vous devez utiliser SQL Server Reporting Services. Dans la plupart des cas, cependant, Azure SQL Database Managed Instance peut fournir tout ce que vous devez migrer à partir de serveurs de SQL Server sur site, afin que la migration vers une machine virtuelle SQL Server doit être votre dernier recours pour essayer.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Utiliser Azure Database Migration Service pour migrer vos bases de données relationnelles vers Azure 

Vous pouvez utiliser Azure Database Migration Service pour migrer des bases de données relationnelles telles que SQL Server, Oracle et MySQL vers Azure, si votre base de données cible est Azure SQL Database, Azure SQL Database Managed Instance ou SQL Server sur une machine virtuelle Azure.

Le flux de travail automatisé, avec le rapport d’évaluation, vous guide dans les modifications que vous devez faire avant de migrer la base de données. Lorsque vous êtes prêt, le service migre la base de données source vers Azure.

Chaque fois que vous modifiez un SGBDR d’origine, vous devrez peut-être tester à nouveau. Vous devrez peut-être modifier le code de mappage objet-relationnel (ORM) dans votre application, en fonction des résultats des tests ou de phrases SQL.

Si vous avez une autre base de données (par exemple, IBM DB2) et vous optez pour une approche de lift- and -shift, vous souhaiterez continuer à utiliser ces bases de données en tant que machines virtuelles IaaS dans Azure, sauf si vous êtes prêt à effectuer une migration de données plus complexe. Une migration de données plus complexe nécessite des efforts supplémentaires, car vous serez migration à un type de base de données différente avec le nouveau schéma et les bibliothèques de programmation différents.

Pour savoir comment migrer des bases de données à l’aide d’Azure Database Migration Service, consultez [migrez vers le cloud plus rapidement avec Azure SQL Database Managed Instance et Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Ressources supplémentaires

- **Choisir une option de SQL Server cloud : Base de données SQL Azure (PaaS) ou SQL Server sur machine virtuelle Azure (IaaS)**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **Migrez vers le cloud plus rapidement avec Azure SQL DB Managed Instance et le Service de Migration de base de données**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **Migration de base de données SQL Server vers SQL Database dans le cloud**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Azure SQL Database**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **SQL Server sur des machines virtuelles**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [Précédent](lift-and-shift-existing-apps-azure-iaas.md)
> [Suivant](modernize-existing-apps-to-cloud-optimized/index.md)
