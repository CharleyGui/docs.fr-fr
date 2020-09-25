---
title: Propriété et séparation des schémas utilisateur dans SQL Server
description: Découvrez comment la séparation utilisateur-schéma permet de gérer SQL Server autorisations d’objet de base de données. Les schémas regroupent les objets dans des espaces de noms distincts.
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: e92799237a90c502aa4000d8d4027df522aa0d87
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183141"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a><span data-ttu-id="10765-104">Propriété et séparation des schémas utilisateur dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="10765-104">Ownership and User-Schema Separation in SQL Server</span></span>

<span data-ttu-id="10765-105">Il existe un concept essentiel relative à la sécurité de SQL Server, selon lequel les propriétaires d'objets disposent d'autorisations irrévocables pour les administrer.</span><span class="sxs-lookup"><span data-stu-id="10765-105">A core concept of SQL Server security is that owners of objects have irrevocable permissions to administer them.</span></span> <span data-ttu-id="10765-106">Vous ne pouvez pas supprimer les privilèges d’un propriétaire d’objets et vous ne pouvez pas supprimer des utilisateurs d’une base de données dans laquelle se trouvent des objets qui leur appartiennent.</span><span class="sxs-lookup"><span data-stu-id="10765-106">You cannot remove privileges from an object owner, and you cannot drop users from a database if they own objects in it.</span></span>  
  
## <a name="user-schema-separation"></a><span data-ttu-id="10765-107">Séparation utilisateur-schéma</span><span class="sxs-lookup"><span data-stu-id="10765-107">User-Schema Separation</span></span>  

 <span data-ttu-id="10765-108">La séparation utilisateur-schéma permet plus de souplesse dans la gestion des autorisations d'objet de base de données.</span><span class="sxs-lookup"><span data-stu-id="10765-108">User-schema separation allows for more flexibility in managing database object permissions.</span></span> <span data-ttu-id="10765-109">Un *schéma* est un conteneur nommé pour les objets de base de données, qui vous permet de regrouper des objets dans des espaces de noms distincts.</span><span class="sxs-lookup"><span data-stu-id="10765-109">A *schema* is a named container for database objects, which allows you to group objects into separate namespaces.</span></span> <span data-ttu-id="10765-110">Par exemple, l'exemple de base de données AdventureWorks contient des schémas pour Production, Sales et HumanResources.</span><span class="sxs-lookup"><span data-stu-id="10765-110">For example, the AdventureWorks sample database contains schemas for Production, Sales, and HumanResources.</span></span>  
  
 <span data-ttu-id="10765-111">La syntaxe de dénomination en quatre parties destinée à faire référence à des objets spécifie le nom de schéma.</span><span class="sxs-lookup"><span data-stu-id="10765-111">The four-part naming syntax for referring to objects specifies the schema name.</span></span>  
  
```text
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a><span data-ttu-id="10765-112">Propriétaires et autorisations de schéma</span><span class="sxs-lookup"><span data-stu-id="10765-112">Schema Owners and Permissions</span></span>  

 <span data-ttu-id="10765-113">Les schémas peuvent appartenir à n'importe quelle principal de sécurité de base de données, tandis qu'une principal de sécurité unique peut posséder plusieurs schémas.</span><span class="sxs-lookup"><span data-stu-id="10765-113">Schemas can be owned by any database principal, and a single principal can own multiple schemas.</span></span> <span data-ttu-id="10765-114">Vous pouvez appliquer des règles de sécurité à un schéma, dont hériteront tous les objets du schéma.</span><span class="sxs-lookup"><span data-stu-id="10765-114">You can apply security rules to a schema, which are inherited by all objects in the schema.</span></span> <span data-ttu-id="10765-115">Une fois que vous avez défini des autorisations d'accès pour un schéma, elles sont automatiquement appliquées lors de l'ajout de nouveaux objets au schéma.</span><span class="sxs-lookup"><span data-stu-id="10765-115">Once you set up access permissions for a schema, those permissions are automatically applied as new objects are added to the schema.</span></span> <span data-ttu-id="10765-116">Un schéma par défaut peut être affecté aux utilisateurs, et plusieurs utilisateurs de base de données peuvent partager le même schéma.</span><span class="sxs-lookup"><span data-stu-id="10765-116">Users can be assigned a default schema, and multiple database users can share the same schema.</span></span>  
  
 <span data-ttu-id="10765-117">Par défaut, lorsque des développeurs créent des objets dans un schéma, ces objets appartiennent à la principal de sécurité qui possède le schéma, et non aux développeurs.</span><span class="sxs-lookup"><span data-stu-id="10765-117">By default, when developers create objects in a schema, the objects are owned by the security principal that owns the schema, not the developer.</span></span> <span data-ttu-id="10765-118">La propriété d'objet peut être transférée avec l'instruction Transact-SQL ALTER AUTHORIZATION.</span><span class="sxs-lookup"><span data-stu-id="10765-118">Object ownership can be transferred with ALTER AUTHORIZATION Transact-SQL statement.</span></span> <span data-ttu-id="10765-119">Un schéma peut également contenir des objets qui appartiennent à différents utilisateurs et disposent d'autorisations plus précises que celles affectées au schéma, même si cela n'est pas recommandé car la gestion des autorisations devient alors plus complexe.</span><span class="sxs-lookup"><span data-stu-id="10765-119">A schema can also contain objects that are owned by different users and have more granular permissions than those assigned to the schema, although this is not recommended because it adds complexity to managing permissions.</span></span> <span data-ttu-id="10765-120">Les objets peuvent être déplacés entre plusieurs schémas et la propriété de schéma peut être transférée entre plusieurs entités.</span><span class="sxs-lookup"><span data-stu-id="10765-120">Objects can be moved between schemas, and schema ownership can be transferred between principals.</span></span> <span data-ttu-id="10765-121">Les utilisateurs de base de données peuvent être supprimés sans affecter les schémas.</span><span class="sxs-lookup"><span data-stu-id="10765-121">Database users can be dropped without affecting schemas.</span></span>  
  
### <a name="built-in-schemas"></a><span data-ttu-id="10765-122">Schémas intégrés</span><span class="sxs-lookup"><span data-stu-id="10765-122">Built-In Schemas</span></span>  

 <span data-ttu-id="10765-123">SQL Server est livré avec six schémas prédéfinis qui possèdent les mêmes noms que les utilisateurs et les rôles de base de données intégrés.</span><span class="sxs-lookup"><span data-stu-id="10765-123">SQL Server ships with ten pre-defined schemas that have the same names as the built-in database users and roles.</span></span> <span data-ttu-id="10765-124">Ils sont principalement destinés à la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="10765-124">These exist mainly for backward compatibility.</span></span> <span data-ttu-id="10765-125">Vous pouvez supprimer les schémas qui possèdent les mêmes noms que ceux des rôles de base de données fixes si vous n’en avez pas besoin.</span><span class="sxs-lookup"><span data-stu-id="10765-125">You can drop the schemas that have the same names as the fixed database roles if you do not need them.</span></span> <span data-ttu-id="10765-126">Par contre, vous ne pouvez pas déposer les schémas suivants :</span><span class="sxs-lookup"><span data-stu-id="10765-126">You cannot drop the following schemas:</span></span>  
  
- `dbo`  
  
- `guest`  
  
- `sys`  
  
- `INFORMATION_SCHEMA`  
  
 <span data-ttu-id="10765-127">Si vous les supprimez de la base de données model, ils n'apparaîtront pas dans les nouvelles bases de données.</span><span class="sxs-lookup"><span data-stu-id="10765-127">If you drop them from the model database, they will not appear in new databases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10765-128">Les schémas `sys` et `INFORMATION_SCHEMA` sont réservés pour les objets système.</span><span class="sxs-lookup"><span data-stu-id="10765-128">The `sys` and `INFORMATION_SCHEMA` schemas are reserved for system objects.</span></span> <span data-ttu-id="10765-129">Vous ne pouvez pas créer d’objets dans ces schémas et vous ne pouvez pas les déposer.</span><span class="sxs-lookup"><span data-stu-id="10765-129">You cannot create objects in these schemas and you cannot drop them.</span></span>  
  
#### <a name="the-dbo-schema"></a><span data-ttu-id="10765-130">Schéma dbo</span><span class="sxs-lookup"><span data-stu-id="10765-130">The dbo Schema</span></span>  

 <span data-ttu-id="10765-131">Le schéma `dbo` constitue le schéma par défaut d'une base de données qui vient d'être créée.</span><span class="sxs-lookup"><span data-stu-id="10765-131">The `dbo` schema is the default schema for a newly created database.</span></span> <span data-ttu-id="10765-132">Le schéma `dbo` appartient au compte d'utilisateur `dbo`.</span><span class="sxs-lookup"><span data-stu-id="10765-132">The `dbo` schema is owned by the `dbo` user account.</span></span> <span data-ttu-id="10765-133">Par défaut, les utilisateurs créés avec la commande Transact-SQL CREATE USER ont `dbo` en tant que schéma par défaut.</span><span class="sxs-lookup"><span data-stu-id="10765-133">By default, users created with the CREATE USER Transact-SQL command have `dbo` as their default schema.</span></span>  
  
 <span data-ttu-id="10765-134">Les utilisateurs à qui est affecté le schéma `dbo` n'héritent pas des autorisations du compte d'utilisateur `dbo`.</span><span class="sxs-lookup"><span data-stu-id="10765-134">Users who are assigned the `dbo` schema do not inherit the permissions of the `dbo` user account.</span></span> <span data-ttu-id="10765-135">Les utilisateurs n'héritent d'aucune autorisation provenant d'un schéma. En effet, ce sont les objets de base de données contenus dans le schéma qui héritent des autorisations du schéma.</span><span class="sxs-lookup"><span data-stu-id="10765-135">No permissions are inherited from a schema by users; schema permissions are inherited by the database objects contained in the schema.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10765-136">Lorsque des objets de base de données sont référencés à l'aide d'un nom en une partie dans SQL Server consulte d'abord le schéma par défaut de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="10765-136">When database objects are referenced by using a one-part name, SQL Server first looks in the user's default schema.</span></span> <span data-ttu-id="10765-137">Si l'objet y est introuvable, SQL Server recherche ensuite dans le schéma `dbo`.</span><span class="sxs-lookup"><span data-stu-id="10765-137">If the object is not found there, SQL Server looks next in the `dbo` schema.</span></span> <span data-ttu-id="10765-138">Si l'objet ne se trouve pas non plus dans le schéma `dbo`, une erreur est retournée.</span><span class="sxs-lookup"><span data-stu-id="10765-138">If the object is not in the `dbo` schema, an error is returned.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="10765-139">Ressources externes</span><span class="sxs-lookup"><span data-stu-id="10765-139">External Resources</span></span>  

 <span data-ttu-id="10765-140">Pour plus d'informations sur la propriété d'objet et les schémas, voir les ressources suivantes.</span><span class="sxs-lookup"><span data-stu-id="10765-140">For more information on object ownership and schemas, see the following resources.</span></span>  
  
|<span data-ttu-id="10765-141">Ressource</span><span class="sxs-lookup"><span data-stu-id="10765-141">Resource</span></span>|<span data-ttu-id="10765-142">Description</span><span class="sxs-lookup"><span data-stu-id="10765-142">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="10765-143">[Séparation du schéma et de l’utilisateur](/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="10765-143">[User-Schema Separation](/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))</span></span>|<span data-ttu-id="10765-144">Décrit les modifications introduites par la séparation utilisateur-schéma.</span><span class="sxs-lookup"><span data-stu-id="10765-144">Describes the changes introduced by user-schema separation.</span></span> <span data-ttu-id="10765-145">Inclut un nouveau comportement, son impact sur la propriété, des affichages catalogue et des autorisations.</span><span class="sxs-lookup"><span data-stu-id="10765-145">Includes new behavior, its impact on ownership, catalog views, and permissions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10765-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10765-146">See also</span></span>

- [<span data-ttu-id="10765-147">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="10765-147">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="10765-148">Scénarios de sécurité des applications dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="10765-148">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="10765-149">Authentification dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="10765-149">Authentication in SQL Server</span></span>](authentication-in-sql-server.md)
- [<span data-ttu-id="10765-150">Serveur et rôles de base de données dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="10765-150">Server and Database Roles in SQL Server</span></span>](server-and-database-roles-in-sql-server.md)
- [<span data-ttu-id="10765-151">Autorisation et permissions dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="10765-151">Authorization and Permissions in SQL Server</span></span>](authorization-and-permissions-in-sql-server.md)
- [<span data-ttu-id="10765-152">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="10765-152">ADO.NET Overview</span></span>](../ado-net-overview.md)
