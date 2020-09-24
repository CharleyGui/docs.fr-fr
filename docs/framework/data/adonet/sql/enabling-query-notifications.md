---
title: Activation de notifications de requête
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 4e9b3a2e1f176a9d01e983bc469cc4032fa5d730
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156171"
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="3142b-102">Activation de notifications de requête</span><span class="sxs-lookup"><span data-stu-id="3142b-102">Enabling Query Notifications</span></span>

<span data-ttu-id="3142b-103">Les applications qui utilisent des notifications de requêtes ont un ensemble commun d’exigences.</span><span class="sxs-lookup"><span data-stu-id="3142b-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="3142b-104">Votre source de données doit être correctement configurée pour prendre en charge les notifications de requête SQL et l'utilisateur doit disposer des autorisations appropriées côté client et côté serveur.</span><span class="sxs-lookup"><span data-stu-id="3142b-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="3142b-105">Pour utiliser des notifications de requêtes, vous devez :</span><span class="sxs-lookup"><span data-stu-id="3142b-105">To use query notifications you must:</span></span>  
  
- <span data-ttu-id="3142b-106">Activer les notifications de requêtes pour votre base de données.</span><span class="sxs-lookup"><span data-stu-id="3142b-106">Enable query notifications for your database.</span></span>  
  
- <span data-ttu-id="3142b-107">Vous assurer que l’ID utilisateur utilisé pour se connecter à la base de données dispose des autorisations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="3142b-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
- <span data-ttu-id="3142b-108">Utilisez un objet <xref:System.Data.SqlClient.SqlCommand> pour exécuter une instruction SELECT valide avec un objet de notification associé, <xref:System.Data.SqlClient.SqlDependency> ou <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="3142b-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
- <span data-ttu-id="3142b-109">Fournissez du code pour traiter la notification si les données surveillées sont modifiées.</span><span class="sxs-lookup"><span data-stu-id="3142b-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="3142b-110">Exigences des notifications de requête</span><span class="sxs-lookup"><span data-stu-id="3142b-110">Query Notifications Requirements</span></span>  

 <span data-ttu-id="3142b-111">Les notifications de requêtes sont prises en charge uniquement pour les instructions SELECT qui répondent à une liste d’exigences suivantes.</span><span class="sxs-lookup"><span data-stu-id="3142b-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="3142b-112">Le tableau suivant fournit des liens vers la documentation sur les notifications de requêtes dans la Documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3142b-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="3142b-113">**Documentation SQL Server**</span><span class="sxs-lookup"><span data-stu-id="3142b-113">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="3142b-114">[Création d’une requête pour notification](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="3142b-114">[Creating a Query for Notification](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="3142b-115">[Considérations relatives à sécurité pour Service Broker](/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="3142b-115">[Security Considerations for Service Broker](/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span></span>  
  
- <span data-ttu-id="3142b-116">[Sécurité et protection (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="3142b-116">[Security and Protection (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span></span>  
  
- <span data-ttu-id="3142b-117">[Considérations relatives à la sécurité pour Notifications Services](/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="3142b-117">[Security Considerations for Notifications Services](/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span></span>  
  
- <span data-ttu-id="3142b-118">[Autorisations associées aux notifications de requêtes](/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="3142b-118">[Query Notification Permissions](/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span></span>  
  
- <span data-ttu-id="3142b-119">[Considérations d’ordre international pour Service Broker](/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="3142b-119">[International Considerations for Service Broker](/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span></span>  
  
- <span data-ttu-id="3142b-120">[Considérations sur la conception de la solution (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="3142b-120">[Solution Design Considerations (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span></span>  
  
- <span data-ttu-id="3142b-121">[Centre d’informations du développeur Service Broker](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="3142b-121">[Service Broker Developer InfoCenter](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="3142b-122">[Guide du développeur (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="3142b-122">[Developer's Guide (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="3142b-123">Activation des notifications de requête pour exécuter l'exemple de code</span><span class="sxs-lookup"><span data-stu-id="3142b-123">Enabling Query Notifications to Run Sample Code</span></span>  

 <span data-ttu-id="3142b-124">Pour activer Service Broker sur la base de données **AdventureWorks** à l’aide de SQL Server Management Studio, exécutez l’instruction Transact-SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="3142b-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="3142b-125">Pour que les exemples de notifications de requêtes s’exécutent correctement, les instructions Transact-SQL suivantes doivent être exécutées sur le serveur de base de données.</span><span class="sxs-lookup"><span data-stu-id="3142b-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="3142b-126">Autorisations de notifications de requête</span><span class="sxs-lookup"><span data-stu-id="3142b-126">Query Notifications Permissions</span></span>  

 <span data-ttu-id="3142b-127">Les utilisateurs qui exécutent des commandes exigeant une notification doivent être INSCRITS à une autorisation de base de données de NOTIFICATIONS DE REQUÊTES sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="3142b-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="3142b-128">Le code côté client qui s’exécute dans une situation de confiance partielle requiert la <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="3142b-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="3142b-129">Le code suivant permet de créer un objet <xref:System.Data.SqlClient.SqlClientPermission> qui définit <xref:System.Security.Permissions.PermissionState> sur <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span><span class="sxs-lookup"><span data-stu-id="3142b-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="3142b-130">La <xref:System.Security.CodeAccessPermission.Demand%2A> force une <xref:System.Security.SecurityException> au moment de l’exécution si l’autorisation a été accordée à tous les appelants au dessus de la pile d’appels.</span><span class="sxs-lookup"><span data-stu-id="3142b-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="3142b-131">Sélection d'un objet notification</span><span class="sxs-lookup"><span data-stu-id="3142b-131">Choosing a Notification Object</span></span>  

 <span data-ttu-id="3142b-132">L’API des notifications de requête fournit deux objets pour traiter les notifications : <xref:System.Data.SqlClient.SqlDependency> et <xref:System.Data.Sql.SqlNotificationRequest>.</span><span class="sxs-lookup"><span data-stu-id="3142b-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="3142b-133">En règle générale, la plupart des applications non ASP.NET doivent utiliser l'objet <xref:System.Data.SqlClient.SqlDependency>.</span><span class="sxs-lookup"><span data-stu-id="3142b-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="3142b-134">Les applications ASP.NET doivent utiliser le <xref:System.Web.Caching.SqlCacheDependency> de niveau supérieur, qui enveloppe <xref:System.Data.SqlClient.SqlDependency> et fournit un cadre pour l'administration des objets notification et cache.</span><span class="sxs-lookup"><span data-stu-id="3142b-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="3142b-135">Utilisation de SqlDependency</span><span class="sxs-lookup"><span data-stu-id="3142b-135">Using SqlDependency</span></span>  

 <span data-ttu-id="3142b-136">Pour utiliser <xref:System.Data.SqlClient.SqlDependency>, Service Broker doit être activé pour la base de données SQL Server utilisée, et les utilisateurs doivent disposer des autorisations nécessaires pour recevoir des notifications.</span><span class="sxs-lookup"><span data-stu-id="3142b-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="3142b-137">Les objets Service Broker, tels que la file d’attente des notifications, sont prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="3142b-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="3142b-138">En outre, <xref:System.Data.SqlClient.SqlDependency> lance automatiquement un thread de travail pour traiter les notifications au fur et à mesure de leur publication dans la file d'attente ; il analyse également le message de Service Broker en exposant les informations comme données d'argument d'événement.</span><span class="sxs-lookup"><span data-stu-id="3142b-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="3142b-139"><xref:System.Data.SqlClient.SqlDependency> doit être initialisé en appelant la méthode `Start` pour établir une dépendance à la base de données.</span><span class="sxs-lookup"><span data-stu-id="3142b-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="3142b-140">Il s’agit d’une méthode statique qui ne doit être appelée qu’une seule fois pendant l’initialisation de l’application pour chaque connexion de base de données requise.</span><span class="sxs-lookup"><span data-stu-id="3142b-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="3142b-141">La méthode `Stop` doit être appelée à la fin de l’application pour chaque connexion de dépendance effectuée.</span><span class="sxs-lookup"><span data-stu-id="3142b-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="3142b-142">Utilisation de SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="3142b-142">Using SqlNotificationRequest</span></span>  

 <span data-ttu-id="3142b-143">Par contre, <xref:System.Data.Sql.SqlNotificationRequest> vous demande d’implémenter vous-même l’infrastructure d’écoute complète.</span><span class="sxs-lookup"><span data-stu-id="3142b-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="3142b-144">En outre, tous les objets Service Broker de prise en charge tels que la file d’attente, le service et les types de messages pris en charge par la file d’attente doivent être définis.</span><span class="sxs-lookup"><span data-stu-id="3142b-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="3142b-145">Cette approche manuelle est utile si votre application requiert des messages de notification spéciaux ou des comportements de notification ou si votre application fait partie d’une plus grande application Service Broker.</span><span class="sxs-lookup"><span data-stu-id="3142b-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3142b-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3142b-146">See also</span></span>

- [<span data-ttu-id="3142b-147">Notifications de requêtes dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="3142b-147">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="3142b-148">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="3142b-148">ADO.NET Overview</span></span>](../ado-net-overview.md)
