---
title: Activation de notifications de requête
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 693e67b4d369eb69b8e0a9dded6decb2d3928459
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554877"
---
# <a name="enabling-query-notifications"></a>Activation de notifications de requête
Les applications qui utilisent des notifications de requêtes ont un ensemble commun d’exigences. Votre source de données doit être correctement configurée pour prendre en charge les notifications de requête SQL et l'utilisateur doit disposer des autorisations appropriées côté client et côté serveur.  
  
 Pour utiliser des notifications de requêtes, vous devez :  
  
- Activer les notifications de requêtes pour votre base de données.  
  
- Vous assurer que l’ID utilisateur utilisé pour se connecter à la base de données dispose des autorisations nécessaires.  
  
- Utilisez un objet <xref:System.Data.SqlClient.SqlCommand> pour exécuter une instruction SELECT valide avec un objet de notification associé, <xref:System.Data.SqlClient.SqlDependency> ou <xref:System.Data.Sql.SqlNotificationRequest>.  
  
- Fournissez du code pour traiter la notification si les données surveillées sont modifiées.  
  
## <a name="query-notifications-requirements"></a>Exigences des notifications de requête  
 Les notifications de requêtes sont prises en charge uniquement pour les instructions SELECT qui répondent à une liste d’exigences suivantes. Le tableau suivant fournit des liens vers la documentation sur les notifications de requêtes dans la Documentation en ligne de SQL Server.  
  
 **Documentation SQL Server**  
  
- [Création d’une requête pour notification](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Considérations relatives à sécurité pour Service Broker](/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
- [Sécurité et protection (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
- [Considérations relatives à la sécurité pour Notifications Services](/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
- [Autorisations associées aux notifications de requêtes](/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
- [Considérations d’ordre international pour Service Broker](/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
- [Considérations sur la conception de la solution (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
- [Centre d’informations du développeur Service Broker](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Guide du développeur (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Activation des notifications de requête pour exécuter l'exemple de code  
 Pour activer Service Broker sur la base de données **AdventureWorks** à l’aide de SQL Server Management Studio, exécutez l’instruction Transact-SQL suivante :  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 Pour que les exemples de notifications de requêtes s’exécutent correctement, les instructions Transact-SQL suivantes doivent être exécutées sur le serveur de base de données.  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Autorisations de notifications de requête  
 Les utilisateurs qui exécutent des commandes exigeant une notification doivent être INSCRITS à une autorisation de base de données de NOTIFICATIONS DE REQUÊTES sur le serveur.  
  
 Le code côté client qui s’exécute dans une situation de confiance partielle requiert la <xref:System.Data.SqlClient.SqlClientPermission>.  
  
 Le code suivant permet de créer un objet <xref:System.Data.SqlClient.SqlClientPermission> qui définit <xref:System.Security.Permissions.PermissionState> sur <xref:System.Security.Permissions.PermissionState.Unrestricted>. La <xref:System.Security.CodeAccessPermission.Demand%2A> force une <xref:System.Security.SecurityException> au moment de l’exécution si l’autorisation a été accordée à tous les appelants au dessus de la pile d’appels.  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a>Sélection d'un objet notification  
 L’API des notifications de requête fournit deux objets pour traiter les notifications : <xref:System.Data.SqlClient.SqlDependency> et <xref:System.Data.Sql.SqlNotificationRequest>. En règle générale, la plupart des applications non ASP.NET doivent utiliser l'objet <xref:System.Data.SqlClient.SqlDependency>. Les applications ASP.NET doivent utiliser le <xref:System.Web.Caching.SqlCacheDependency> de niveau supérieur, qui enveloppe <xref:System.Data.SqlClient.SqlDependency> et fournit un cadre pour l'administration des objets notification et cache.  
  
### <a name="using-sqldependency"></a>Utilisation de SqlDependency  
 Pour utiliser <xref:System.Data.SqlClient.SqlDependency>, Service Broker doit être activé pour la base de données SQL Server utilisée, et les utilisateurs doivent disposer des autorisations nécessaires pour recevoir des notifications. Les objets Service Broker, tels que la file d’attente des notifications, sont prédéfinis.  
  
 En outre, <xref:System.Data.SqlClient.SqlDependency> lance automatiquement un thread de travail pour traiter les notifications au fur et à mesure de leur publication dans la file d'attente ; il analyse également le message de Service Broker en exposant les informations comme données d'argument d'événement. <xref:System.Data.SqlClient.SqlDependency> doit être initialisé en appelant la méthode `Start` pour établir une dépendance à la base de données. Il s’agit d’une méthode statique qui ne doit être appelée qu’une seule fois pendant l’initialisation de l’application pour chaque connexion de base de données requise. La méthode `Stop` doit être appelée à la fin de l’application pour chaque connexion de dépendance effectuée.  
  
### <a name="using-sqlnotificationrequest"></a>Utilisation de SqlNotificationRequest  
 Par contre, <xref:System.Data.Sql.SqlNotificationRequest> vous demande d’implémenter vous-même l’infrastructure d’écoute complète. En outre, tous les objets Service Broker de prise en charge tels que la file d’attente, le service et les types de messages pris en charge par la file d’attente doivent être définis. Cette approche manuelle est utile si votre application requiert des messages de notification spéciaux ou des comportements de notification ou si votre application fait partie d’une plus grande application Service Broker.  
  
## <a name="see-also"></a>Voir aussi

- [Notifications de requêtes dans SQL Server](query-notifications-in-sql-server.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
