---
title: Notifications de requête dans SQL Server
description: Découvrez comment utiliser les notifications de requêtes pour notifier les applications lorsque les données ont changé dans une base de données SQL Server, par exemple, pour actualiser les affichages des applications.
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 43b496db74f7e6fc9bc9f17d946bf34398b32312
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543983"
---
# <a name="query-notifications-in-sql-server"></a>Notifications de requête dans SQL Server
Basées sur l’infrastructure de Service Broker, les notifications de requêtes permettent aux applications d’être notifiées en cas de modification des données. Cette fonctionnalité est particulièrement utile pour les applications qui fournissent un cache d'informations à partir d'une base de données, par exemple une application Web, et qui doivent être notifiées en cas de modification des données sources.  
  
 Il existe trois façons d’implémenter des notifications de requête à l’aide de ADO.NET :  
  
1. L’implémentation de bas niveau est fournie par la classe `SqlNotificationRequest` qui expose les fonctionnalités côté serveur, ce qui vous permet d’exécuter une commande avec une requête de notification.  
  
2. L’implémentation de haut niveau est fournie par la classe `SqlDependency`, qui est une classe qui fournit une abstraction de haut niveau de la fonctionnalité de notification entre l’application source et SQL Server, ce qui vous permet d’utiliser une dépendance pour détecter les modifications apportées au serveur. Généralement, il s'agit de la manière la plus simple et la plus efficace, pour des applications clientes managées, d'exploiter la fonctionnalité de notification de SQL Server en utilisant le fournisseur de données .NET Framework pour SQL Server.  
  
3. De plus, les applications web créées avec ASP.NET 2.0 ou ultérieur peuvent utiliser les classes d’assistance `SqlCacheDependency`.  
  
 Les notifications de requête sont utilisées pour les applications qui doivent actualiser des affichages ou des caches en réponse aux modifications des données sous-jacentes. Microsoft SQL Server permet aux applications .NET Framework d'envoyer une commande à SQL Server et de demander la génération d'une notification si l'exécution de cette commande produit des ensembles de résultats différents de ceux extraits initialement. Les notifications générées au niveau du serveur sont envoyées par l’intermédiaire de files d’attente pour un traitement ultérieur.  
  
 Vous pouvez configurer des notifications pour les instructions SELECT et EXECUTE. Lorsque vous utilisez une instruction EXECUTE, SQL Server enregistre une notification pour la commande exécutée plutôt que l’instruction EXECUTE elle-même. La commande doit satisfaire les exigences et limitations applicables aux instructions SELECT. Quand une commande qui enregistre une notification contient plusieurs instructions, le moteur de base de données crée une notification pour chaque instruction du traitement.  
  
 Si vous développez une application où vous avez besoin de notifications de sous-secondes fiables en cas de modification des données, consultez les sections **planification d’une stratégie de notifications de requêtes efficaces** et **alternatives aux notifications de requête** dans l’article [planification des notifications](/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105)) . Pour plus d’informations sur les notifications et les SQL Server Service Broker de requêtes, consultez les liens suivants vers les Articles de la documentation SQL Server.  
  
 **Documentation SQL Server**  
  
- [Utilisation des notifications de requêtes](/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))  
  
- [Création d’une requête pour notification](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Développement (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))  
  
- [Centre d’informations du développeur Service Broker](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Guide du développeur (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="in-this-section"></a>Dans cette section  
 [Activation des notifications de requêtes](enabling-query-notifications.md)  
 Explique comment utiliser les notifications de requêtes, notamment les exigences pour les activer et les utiliser.  
  
 [SqlDependency dans une application ASP.NET](sqldependency-in-an-aspnet-app.md)  
 Montre comment utiliser les notifications de requêtes à partir d'une application ASP.NET.  
  
 [Détection des modifications avec SqlDependency](detecting-changes-with-sqldependency.md)  
 Montre comment détecter si les résultats de la requête sont différents de ceux qui ont été reçus à l’origine.  
  
 [Exécution de SqlCommand avec un SqlNotificationRequest](sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Illustre la configuration d’un objet <xref:System.Data.SqlClient.SqlCommand> pour utiliser une notification de requête.  
  
## <a name="reference"></a>Informations de référence  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 Décrit la classe <xref:System.Data.Sql.SqlNotificationRequest> et tous ses membres.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 Décrit la classe <xref:System.Data.SqlClient.SqlDependency> et tous ses membres.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 Décrit la classe <xref:System.Web.Caching.SqlCacheDependency> et tous ses membres.  
  
## <a name="see-also"></a>Voir aussi

- [SQL Server et ADO.NET](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
