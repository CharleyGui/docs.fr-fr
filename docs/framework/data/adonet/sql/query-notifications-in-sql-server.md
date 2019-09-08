---
title: Notifications de requête dans SQL Server
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 94171c8dac59fc17b0dd699d87fc043651fa5b7a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791770"
---
# <a name="query-notifications-in-sql-server"></a>Notifications de requête dans SQL Server
Basées sur l'infrastructure Service Broker, les notifications de requête permettent de notifier des applications en cas de modification de données. Cette fonctionnalité est particulièrement utile pour les applications qui génèrent un cache d’informations à partir d’une base de données, telles que les applications Web, et qui doivent être informées en cas de modification des données sources.  
  
 ADO.NET vous permet d'implémenter les notifications de requête de trois manières :  
  
1. L'implémentation de bas niveau est assurée par la classe `SqlNotificationRequest` qui expose les fonctionnalités côté serveur, vous permettant d'exécuter une commande avec une demande de notification.  
  
2. L'implémentation de haut niveau est assurée par la classe `SqlDependency` qui fournit une abstraction de haut niveau des fonctionnalités de notification entre l'application source et SQL Server, ce qui vous permet d'utiliser une dépendance pour détecter des modifications au niveau serveur. Généralement, il s'agit de la manière la plus simple et la plus efficace, pour des applications clientes managées, d'exploiter la fonctionnalité de notification de SQL Server en utilisant le fournisseur de données .NET Framework pour SQL Server.  
  
3. En outre, les applications Web créées à l'aide d'ASP.NET 2.0 ou version ultérieure peuvent utiliser les classes d'assistance `SqlCacheDependency`.  
  
 Les notifications de requête sont utilisées pour les applications qui doivent actualiser des affichages ou des caches suite à l'apport de modifications aux données sous-jacentes. Microsoft SQL Server permet aux applications .NET Framework d'envoyer une commande à SQL Server et de demander la génération d'une notification si l'exécution de cette commande produit des ensembles de résultats différents de ceux extraits initialement. Les notifications générées au niveau du serveur sont envoyées via des files d'attente pour être traitées ultérieurement.  
  
 Vous pouvez configurer des notifications pour les instructions SELECT et EXECUTE. Avec une instruction EXECUTE, SQL Server enregistre une notification pour la commande exécutée et non l'instruction EXECUTE elle-même. La commande doit répondre aux exigences et aux limitations d’une instruction SELECT. Lorsqu'une commande qui enregistre une notification contient plusieurs instructions, le moteur de base de données crée une notification pour chaque instruction du lot.  
  
 Si vous développez une application où vous avez besoin de notifications de sous-secondes fiables en cas de modification des données, consultez les sections **planification d’une stratégie de notifications de requêtes efficaces** et **alternatives aux notifications de requête** dans la [planification de La rubrique notifications](https://go.microsoft.com/fwlink/?LinkId=211984) dans documentation en ligne de SQL Server. Pour plus d'informations sur les notifications de requête et Service Broker de SQL Server, voir les liens aux rubriques ci-dessous dans la documentation en ligne de SQL Server.  
  
 **Documentation SQL Server**  
  
- [Utilisation des notifications de requête](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))  
  
- [Création d’une requête de notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Développement (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))  
  
- [Centre d’informations du développeur Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Guide du développeur (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="in-this-section"></a>Dans cette section  
 [Activation de notifications de requête](enabling-query-notifications.md)  
 Explique comment utiliser des notifications de requête incluant les exigences relatives à leur utilisation et à leur activation.  
  
 [SqlDependency dans une application ASP.NET](sqldependency-in-an-aspnet-app.md)  
 Montre comment utiliser les notifications de requête à partir d'une application ASP.NET.  
  
 [Détection des modifications avec SqlDependency](detecting-changes-with-sqldependency.md)  
 Montre comment détecter lorsque les résultats de la requête seront différents de ceux reçus à l'origine.  
  
 [Exécution de SqlCommand avec une SqlNotificationRequest](sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Illustre la configuration d'un objet <xref:System.Data.SqlClient.SqlCommand> pour travailler avec une notification de requête.  
  
## <a name="reference"></a>Référence  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 Décrit la classe <xref:System.Data.Sql.SqlNotificationRequest> et tous ses membres.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 Décrit la classe <xref:System.Data.SqlClient.SqlDependency> et tous ses membres.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 Décrit la classe <xref:System.Web.Caching.SqlCacheDependency> et tous ses membres.  
  
## <a name="see-also"></a>Voir aussi

- [SQL Server et ADO.NET](index.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
