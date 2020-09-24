---
title: Activation de l'accès entre bases de données dans SQL Server
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: 6ea1ed9a6faa39df0a4f9a4a353bf34c7f5ba601
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156262"
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="1ae12-102">Activation de l'accès entre bases de données dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ae12-102">Enabling Cross-Database Access in SQL Server</span></span>

<span data-ttu-id="1ae12-103">Le chaînage des propriétés des bases de données croisées se produit lorsqu'une procédure dans une base de données repose sur des objets appartenant à une autre base de données.</span><span class="sxs-lookup"><span data-stu-id="1ae12-103">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="1ae12-104">La chaîne des propriétés des bases de données croisées fonctionne de la même manière que le chaînage des propriétés dans une seule base de données, sauf qu'une chaîne de propriétés continue nécessite le mappage de tous les propriétaires d'objets au même compte de connexion.</span><span class="sxs-lookup"><span data-stu-id="1ae12-104">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="1ae12-105">Si l'objet source de la base de données source et les objets cibles des bases de données cibles appartiennent au même compte de connexion, SQL Server ne vérifie pas les autorisations sur les objets cibles.</span><span class="sxs-lookup"><span data-stu-id="1ae12-105">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="1ae12-106">Désactivé par défaut</span><span class="sxs-lookup"><span data-stu-id="1ae12-106">Off By Default</span></span>  

 <span data-ttu-id="1ae12-107">Le chaînage des propriétés des bases de données est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="1ae12-107">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="1ae12-108">Microsoft vous recommande de désactiver le chaînage des propriétés des bases de données croisées, car il vous expose aux risques de sécurité suivants :</span><span class="sxs-lookup"><span data-stu-id="1ae12-108">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
- <span data-ttu-id="1ae12-109">Les propriétaires et les membres de base de données des rôles de base de données `db_ddladmin` ou `db_owners` peuvent créer des objets appartenant à d'autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="1ae12-109">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="1ae12-110">Ces objets peuvent potentiellement viser des objets dans d'autres bases de données.</span><span class="sxs-lookup"><span data-stu-id="1ae12-110">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="1ae12-111">Cela signifie que si vous activez le chaînage des propriétés des bases de données croisées, vous devez faire totalement confiance aux utilisateurs dans toutes les bases de données.</span><span class="sxs-lookup"><span data-stu-id="1ae12-111">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
- <span data-ttu-id="1ae12-112">Les utilisateurs avec l'autorisation CREATE DATABASE peuvent créer de nouvelles bases de données et attacher les bases de données existantes.</span><span class="sxs-lookup"><span data-stu-id="1ae12-112">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="1ae12-113">Si le chaînage des propriétés des bases de données croisées est activé, ces utilisateurs peuvent accéder à des objets dans d'autres bases de données pour lesquels ils n'ont pas de privilèges à partir des bases de données qu'ils ont récemment créées ou attachées.</span><span class="sxs-lookup"><span data-stu-id="1ae12-113">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="1ae12-114">Activation du chaînage des propriétés des bases de données croisées</span><span class="sxs-lookup"><span data-stu-id="1ae12-114">Enabling Cross-database Ownership Chaining</span></span>  

 <span data-ttu-id="1ae12-115">L'activation du chaînage des propriétés des bases de données croisées doit être réservée aux environnements dans lesquels vous pouvez faire totalement confiance aux utilisateurs disposant de privilèges élevés.</span><span class="sxs-lookup"><span data-stu-id="1ae12-115">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="1ae12-116">Vous pouvez configurer l'activation au cours de l'installation pour l'ensemble des bases de données, ou de manière sélective pour des bases de données spécifiques à l'aide des commandes Transact-SQL `sp_configure` et `ALTER DATABASE`.</span><span class="sxs-lookup"><span data-stu-id="1ae12-116">It can be configured during setup for all databases, or selectively for specific databases using the Transact-SQL commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="1ae12-117">Pour configurer de manière sélective le chaînage des propriétés des bases de données croisées, utilisez `sp_configure` afin de désactiver cette option pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="1ae12-117">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="1ae12-118">Puis, utilisez la commande ALTER DATABASE avec SET DB_CHAINING ON afin de configurer le chaînage des propriétés des bases de données croisées uniquement pour les bases de données qui le nécessitent.</span><span class="sxs-lookup"><span data-stu-id="1ae12-118">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="1ae12-119">L'exemple suivant active le chaînage des propriétés des bases de données pour toutes les bases de données :</span><span class="sxs-lookup"><span data-stu-id="1ae12-119">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```sql
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="1ae12-120">L'exemple suivant active le chaînage des propriétés des bases de données de bases de données spécifiques :</span><span class="sxs-lookup"><span data-stu-id="1ae12-120">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```sql
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="1ae12-121">SQL dynamique</span><span class="sxs-lookup"><span data-stu-id="1ae12-121">Dynamic SQL</span></span>  

 <span data-ttu-id="1ae12-122">Le chaînage des propriétés des bases de données croisées ne fonctionne pas dans les cas où des instructions SQL créées dynamiquement sont exécutées sauf si le même utilisateur existe dans les deux bases de données.</span><span class="sxs-lookup"><span data-stu-id="1ae12-122">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="1ae12-123">Il est possible de contourner cette restriction dans SQL Server en créant une procédure stockée qui accède aux données dans une autre base de données et en signant la procédure avec un certificat qui existe dans les deux bases de données.</span><span class="sxs-lookup"><span data-stu-id="1ae12-123">You can work around this in SQL Server by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="1ae12-124">Cela permet aux utilisateurs d’accéder aux ressources de base de données utilisées par la procédure sans leur accorder un accès ou des autorisations de base de données.</span><span class="sxs-lookup"><span data-stu-id="1ae12-124">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="1ae12-125">Ressources externes</span><span class="sxs-lookup"><span data-stu-id="1ae12-125">External Resources</span></span>  

 <span data-ttu-id="1ae12-126">Pour plus d'informations, consultez les ressources ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="1ae12-126">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="1ae12-127">Ressource</span><span class="sxs-lookup"><span data-stu-id="1ae12-127">Resource</span></span>|<span data-ttu-id="1ae12-128">Description</span><span class="sxs-lookup"><span data-stu-id="1ae12-128">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="1ae12-129">[Extension de l’emprunt d’identité de base de données à l’aide de l’option Execute As](/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) et [cross db ownership chaining](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).</span><span class="sxs-lookup"><span data-stu-id="1ae12-129">[Extending Database Impersonation by Using EXECUTE AS](/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) and [Cross DB Ownership Chaining Option](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).</span></span>|<span data-ttu-id="1ae12-130">Les articles décrivent comment configurer le chaînage des propriétés des bases de données croisées pour une instance de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1ae12-130">Articles describe how to configure cross-database ownership chaining for an instance of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ae12-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ae12-131">See also</span></span>

- [<span data-ttu-id="1ae12-132">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1ae12-132">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="1ae12-133">Vue d'ensemble de la sécurité SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ae12-133">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="1ae12-134">Gestion des autorisations avec les procédures stockées dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ae12-134">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="1ae12-135">Écriture d’une instruction SQL dynamique sécurisée dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ae12-135">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="1ae12-136">Signature de procédures stockées dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="1ae12-136">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="1ae12-137">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1ae12-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
