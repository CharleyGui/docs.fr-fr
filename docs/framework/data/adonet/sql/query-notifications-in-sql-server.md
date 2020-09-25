---
title: Notifications de requête dans SQL Server
description: Découvrez comment utiliser les notifications de requêtes pour notifier les applications lorsque les données ont changé dans une base de données SQL Server, par exemple, pour actualiser les affichages des applications.
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 8001f75d7e278a965b6e8e00e4b9af7b770a8bb5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183089"
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="6c83c-103">Notifications de requête dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="6c83c-103">Query Notifications in SQL Server</span></span>

<span data-ttu-id="6c83c-104">Basées sur l’infrastructure de Service Broker, les notifications de requêtes permettent aux applications d’être notifiées en cas de modification des données.</span><span class="sxs-lookup"><span data-stu-id="6c83c-104">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="6c83c-105">Cette fonctionnalité est particulièrement utile pour les applications qui fournissent un cache d'informations à partir d'une base de données, par exemple une application Web, et qui doivent être notifiées en cas de modification des données sources.</span><span class="sxs-lookup"><span data-stu-id="6c83c-105">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="6c83c-106">Il existe trois façons d’implémenter des notifications de requête à l’aide de ADO.NET :</span><span class="sxs-lookup"><span data-stu-id="6c83c-106">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1. <span data-ttu-id="6c83c-107">L’implémentation de bas niveau est fournie par la classe `SqlNotificationRequest` qui expose les fonctionnalités côté serveur, ce qui vous permet d’exécuter une commande avec une requête de notification.</span><span class="sxs-lookup"><span data-stu-id="6c83c-107">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2. <span data-ttu-id="6c83c-108">L’implémentation de haut niveau est fournie par la classe `SqlDependency`, qui est une classe qui fournit une abstraction de haut niveau de la fonctionnalité de notification entre l’application source et SQL Server, ce qui vous permet d’utiliser une dépendance pour détecter les modifications apportées au serveur.</span><span class="sxs-lookup"><span data-stu-id="6c83c-108">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="6c83c-109">Généralement, il s'agit de la manière la plus simple et la plus efficace, pour des applications clientes managées, d'exploiter la fonctionnalité de notification de SQL Server en utilisant le fournisseur de données .NET Framework pour SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6c83c-109">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3. <span data-ttu-id="6c83c-110">De plus, les applications web créées avec ASP.NET 2.0 ou ultérieur peuvent utiliser les classes d’assistance `SqlCacheDependency`.</span><span class="sxs-lookup"><span data-stu-id="6c83c-110">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="6c83c-111">Les notifications de requête sont utilisées pour les applications qui doivent actualiser des affichages ou des caches en réponse aux modifications des données sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="6c83c-111">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="6c83c-112">Microsoft SQL Server permet aux applications .NET Framework d'envoyer une commande à SQL Server et de demander la génération d'une notification si l'exécution de cette commande produit des ensembles de résultats différents de ceux extraits initialement.</span><span class="sxs-lookup"><span data-stu-id="6c83c-112">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="6c83c-113">Les notifications générées au niveau du serveur sont envoyées par l’intermédiaire de files d’attente pour un traitement ultérieur.</span><span class="sxs-lookup"><span data-stu-id="6c83c-113">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="6c83c-114">Vous pouvez configurer des notifications pour les instructions SELECT et EXECUTE.</span><span class="sxs-lookup"><span data-stu-id="6c83c-114">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="6c83c-115">Lorsque vous utilisez une instruction EXECUTE, SQL Server enregistre une notification pour la commande exécutée plutôt que l’instruction EXECUTE elle-même.</span><span class="sxs-lookup"><span data-stu-id="6c83c-115">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="6c83c-116">La commande doit satisfaire les exigences et limitations applicables aux instructions SELECT.</span><span class="sxs-lookup"><span data-stu-id="6c83c-116">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="6c83c-117">Quand une commande qui enregistre une notification contient plusieurs instructions, le moteur de base de données crée une notification pour chaque instruction du traitement.</span><span class="sxs-lookup"><span data-stu-id="6c83c-117">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="6c83c-118">Si vous développez une application où vous avez besoin de notifications de sous-secondes fiables en cas de modification des données, consultez les sections **planification d’une stratégie de notifications de requêtes efficaces** et **alternatives aux notifications de requête** dans l’article [planification des notifications](/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105)) .</span><span class="sxs-lookup"><span data-stu-id="6c83c-118">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105)) article.</span></span> <span data-ttu-id="6c83c-119">Pour plus d’informations sur les notifications et les SQL Server Service Broker de requêtes, consultez les liens suivants vers les Articles de la documentation SQL Server.</span><span class="sxs-lookup"><span data-stu-id="6c83c-119">For more information about Query Notifications and SQL Server Service Broker, see the following links to articles in the SQL Server documentation.</span></span>  
  
 <span data-ttu-id="6c83c-120">**Documentation SQL Server**</span><span class="sxs-lookup"><span data-stu-id="6c83c-120">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="6c83c-121">[Utilisation des notifications de requêtes](/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="6c83c-121">[Using Query Notifications](/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span></span>  
  
- <span data-ttu-id="6c83c-122">[Création d’une requête pour notification](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="6c83c-122">[Creating a Query for Notification](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="6c83c-123">[Développement (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="6c83c-123">[Development (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span></span>  
  
- <span data-ttu-id="6c83c-124">[Centre d’informations du développeur Service Broker](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="6c83c-124">[Service Broker Developer InfoCenter](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="6c83c-125">[Guide du développeur (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="6c83c-125">[Developer's Guide (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c83c-126">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6c83c-126">In This Section</span></span>  

 [<span data-ttu-id="6c83c-127">Activation des notifications de requêtes</span><span class="sxs-lookup"><span data-stu-id="6c83c-127">Enabling Query Notifications</span></span>](enabling-query-notifications.md)  
 <span data-ttu-id="6c83c-128">Explique comment utiliser les notifications de requêtes, notamment les exigences pour les activer et les utiliser.</span><span class="sxs-lookup"><span data-stu-id="6c83c-128">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="6c83c-129">SqlDependency dans une application ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6c83c-129">SqlDependency in an ASP.NET Application</span></span>](sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="6c83c-130">Montre comment utiliser les notifications de requêtes à partir d'une application ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6c83c-130">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="6c83c-131">Détection des modifications avec SqlDependency</span><span class="sxs-lookup"><span data-stu-id="6c83c-131">Detecting Changes with SqlDependency</span></span>](detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="6c83c-132">Montre comment détecter si les résultats de la requête sont différents de ceux qui ont été reçus à l’origine.</span><span class="sxs-lookup"><span data-stu-id="6c83c-132">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="6c83c-133">Exécution de SqlCommand avec un SqlNotificationRequest</span><span class="sxs-lookup"><span data-stu-id="6c83c-133">SqlCommand Execution with a SqlNotificationRequest</span></span>](sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="6c83c-134">Illustre la configuration d’un objet <xref:System.Data.SqlClient.SqlCommand> pour utiliser une notification de requête.</span><span class="sxs-lookup"><span data-stu-id="6c83c-134">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6c83c-135">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="6c83c-135">Reference</span></span>  

 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="6c83c-136">Décrit la classe <xref:System.Data.Sql.SqlNotificationRequest> et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="6c83c-136">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="6c83c-137">Décrit la classe <xref:System.Data.SqlClient.SqlDependency> et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="6c83c-137">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="6c83c-138">Décrit la classe <xref:System.Web.Caching.SqlCacheDependency> et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="6c83c-138">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c83c-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c83c-139">See also</span></span>

- [<span data-ttu-id="6c83c-140">SQL Server et ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6c83c-140">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="6c83c-141">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6c83c-141">ADO.NET Overview</span></span>](../ado-net-overview.md)
