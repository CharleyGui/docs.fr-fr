---
title: Attribution d'autorisations de niveau ligne dans SQL Server
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 0b34eaee4b66a2be82049816f0a98b9f53012303
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554851"
---
# <a name="granting-row-level-permissions-in-sql-server"></a><span data-ttu-id="90994-102">Attribution d'autorisations de niveau ligne dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="90994-102">Granting Row-Level Permissions in SQL Server</span></span>

<span data-ttu-id="90994-103">Dans certains scénarios, il est nécessaire de contrôler l’accès aux données plus précisément qu’en se contentant d’accorder, de révoquer ou de refuser des autorisations.</span><span class="sxs-lookup"><span data-stu-id="90994-103">In some scenarios, there is a requirement to control access to data at a more granular level than what simply granting, revoking, or denying permissions provides.</span></span> <span data-ttu-id="90994-104">Par exemple, l’application de base de données d’un hôpital peut nécessiter que chaque médecin ne puisse accéder qu’aux informations de ses propres patients.</span><span class="sxs-lookup"><span data-stu-id="90994-104">For example, a hospital database application may require individual Doctors to be restricted to accessing information related to only their patients.</span></span> <span data-ttu-id="90994-105">Des scénarios similaires existent dans de nombreux environnements, notamment dans les applications financières, juridiques, publiques et militaires.</span><span class="sxs-lookup"><span data-stu-id="90994-105">Similar requirements exist in many environments, including finance, law, government, and military applications.</span></span> <span data-ttu-id="90994-106">Pour gérer ces scénarios, SQL Server 2016 propose une fonctionnalité [Sécurité au niveau des lignes](/sql/relational-databases/security/row-level-security) qui simplifie et centralise la logique d’accès au niveau des lignes dans une stratégie de sécurité.</span><span class="sxs-lookup"><span data-stu-id="90994-106">To help address these scenarios, SQL Server 2016 provides a [Row-Level Security](/sql/relational-databases/security/row-level-security) feature that simplifies and centralizes row-level access logic in a security policy.</span></span> <span data-ttu-id="90994-107">Pour les versions antérieures de SQL Server, une fonctionnalité similaire peut être obtenue à l’aide de vues permettant de mettre en œuvre un filtrage au niveau des lignes.</span><span class="sxs-lookup"><span data-stu-id="90994-107">For earlier versions of SQL Server, similar functionality can be achieved by using views to enact row-level filtering.</span></span>

## <a name="implementing-row-level-filtering"></a><span data-ttu-id="90994-108">Implémentation du filtrage au niveau des lignes</span><span class="sxs-lookup"><span data-stu-id="90994-108">Implementing Row-level Filtering</span></span>

<span data-ttu-id="90994-109">Le filtrage au niveau des lignes est utilisé pour les applications qui stockent des informations dans une seule table, comme dans l’exemple de l’hôpital ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="90994-109">Row-level filtering is used for applications storing information in a single table like in the hospital example above.</span></span> <span data-ttu-id="90994-110">Pour implémenter le filtrage au niveau des lignes, chaque ligne est associée à une colonne qui définit un paramètre de différenciation, comme un nom d’utilisateur, une étiquette ou tout autre identificateur.</span><span class="sxs-lookup"><span data-stu-id="90994-110">To implement row-level filtering each row has a column that defines a differentiating parameter, such as a user name, label or other identifier.</span></span> <span data-ttu-id="90994-111">Vous créez une stratégie de sécurité ou une vue sur la table, qui filtre les lignes auxquelles l’utilisateur a accès.</span><span class="sxs-lookup"><span data-stu-id="90994-111">You create either a security policy or a view on the table, which filters the rows that the user can access.</span></span> <span data-ttu-id="90994-112">Vous créez ensuite des procédures stockées paramétrées qui contrôlent les types de requêtes que l’utilisateur peut exécuter.</span><span class="sxs-lookup"><span data-stu-id="90994-112">You then create parameterized stored procedures, which control the types of queries the user can execute.</span></span>

<span data-ttu-id="90994-113">L’exemple suivant décrit comment configurer le filtrage au niveau des lignes à partir d’un nom d’utilisateur ou d’un nom de connexion.</span><span class="sxs-lookup"><span data-stu-id="90994-113">The following example describes how to configure row-level filtering based on a user or login name:</span></span>

- <span data-ttu-id="90994-114">Créez la table en ajoutant une colonne pour stocker le nom.</span><span class="sxs-lookup"><span data-stu-id="90994-114">Create the table, adding a column to store the name.</span></span>

- <span data-ttu-id="90994-115">Activez le filtrage au niveau des lignes :</span><span class="sxs-lookup"><span data-stu-id="90994-115">Enable row-level filtering:</span></span>

  - <span data-ttu-id="90994-116">Si vous utilisez SQL Server 2016 ou version ultérieure, ou [Azure SQL Database](/azure/sql-database/), créez une stratégie de sécurité qui ajoute un prédicat sur la table pour limiter les lignes retournées à celles qui correspondent à l’utilisateur de base de données actuel (à l’aide de la fonction intégrée CURRENT_USER()) ou au nom de connexion actuel (à l’aide de la fonction intégrée SUSER_SNAME()) :</span><span class="sxs-lookup"><span data-stu-id="90994-116">If you are using SQL Server 2016 or higher, or [Azure SQL Database](/azure/sql-database/), create a security policy that adds a predicate on the table restricting the rows returned to those that match either the current database user (using the CURRENT_USER() built-in function) or the current login name (using the SUSER_SNAME() built-in function):</span></span>

      ```sql
      CREATE SCHEMA Security
      GO

      CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)
          RETURNS TABLE
          WITH SCHEMABINDING
      AS
          RETURN SELECT 1 AS accessResult
          WHERE @UserName = SUSER_SNAME()
      GO

      CREATE SECURITY POLICY Security.userAccessPolicy
          ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,
          ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable
      GO
      ```

  - <span data-ttu-id="90994-117">Si vous utilisez une version de SQL Server antérieure à 2016, vous pouvez obtenir des fonctionnalités similaires à l’aide d’une vue :</span><span class="sxs-lookup"><span data-stu-id="90994-117">If you are using a version of SQL Server prior to 2016, you can achieve similar functionality using a view:</span></span>

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- <span data-ttu-id="90994-118">Créez des procédures stockées pour sélectionner, insérer, mettre à jour et supprimer des données.</span><span class="sxs-lookup"><span data-stu-id="90994-118">Create stored procedures to select, insert, update, and delete data.</span></span> <span data-ttu-id="90994-119">Si le filtrage est imposé par une stratégie de sécurité, les procédures stockées doivent effectuer ces opérations directement sur la table de base. Dans le cas contraire, si le filtrage est imposé par une vue, les procédures stockées doivent plutôt fonctionner sur la vue.</span><span class="sxs-lookup"><span data-stu-id="90994-119">If the filtering is enacted by a security policy, the stored procedures should perform these operations on the base table directly; otherwise, if the filtering is enacted by a view, the stored procedures should instead operate against the view.</span></span> <span data-ttu-id="90994-120">La stratégie de sécurité ou la vue filtre automatiquement les lignes retournées ou modifiées par les requêtes utilisateur, et la procédure stockée fournit une limite de sécurité plus élevée pour empêcher les utilisateurs bénéficiant d’un accès direct aux requêtes d’exécuter des requêtes capables de déduire l’existence des données filtrées.</span><span class="sxs-lookup"><span data-stu-id="90994-120">The security policy or view will automatically filter the rows returned or modified by user queries, and the stored procedure will provide a harder security boundary to prevent users with direct query access from successfully running queries that can infer the existence of filtered data.</span></span>

- <span data-ttu-id="90994-121">Pour les procédures stockées qui insèrent des données, capturez le nom d’utilisateur à l’aide de la même fonction que celle spécifiée dans la stratégie de sécurité ou la vue et insérez cette valeur dans la colonne UserName.</span><span class="sxs-lookup"><span data-stu-id="90994-121">For stored procedures that insert data, capture the user name using the same function specified in the security policy or view, and insert that value into the UserName column.</span></span>

- <span data-ttu-id="90994-122">Refusez au rôle `public` toutes les autorisations sur les tables (et les vues, le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="90994-122">Deny all permissions on the tables (and views, if applicable) to the `public` role.</span></span> <span data-ttu-id="90994-123">Les utilisateurs ne peuvent pas hériter des autorisations d’autres rôles de base de données, car le prédicat de filtre repose sur des noms d’utilisateurs ou de connexion, et non sur des rôles.</span><span class="sxs-lookup"><span data-stu-id="90994-123">Users will not be able to inherit permissions from other database roles, because the filter predicate is based on user or login names, not on roles.</span></span>

- <span data-ttu-id="90994-124">Accordez aux rôles de base de données l'autorisation EXECUTE sur les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="90994-124">Grant EXECUTE on the stored procedures to database roles.</span></span> <span data-ttu-id="90994-125">Les utilisateurs ne peuvent accéder aux données que par le biais des procédures stockées fournies.</span><span class="sxs-lookup"><span data-stu-id="90994-125">Users can only access data through the stored procedures provided.</span></span>

## <a name="see-also"></a><span data-ttu-id="90994-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90994-126">See also</span></span>

- [<span data-ttu-id="90994-127">Sécurité au niveau des lignes</span><span class="sxs-lookup"><span data-stu-id="90994-127">Row-Level Security</span></span>](/sql/relational-databases/security/row-level-security)
- [<span data-ttu-id="90994-128">Sécurisation des applications ADO.NET</span><span class="sxs-lookup"><span data-stu-id="90994-128">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="90994-129">Vue d'ensemble de la sécurité SQL Server</span><span class="sxs-lookup"><span data-stu-id="90994-129">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="90994-130">Scénarios de sécurité des applications dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="90994-130">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="90994-131">Gestion des autorisations avec les procédures stockées dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="90994-131">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="90994-132">Écriture d’une instruction SQL dynamique sécurisée dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="90994-132">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="90994-133">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="90994-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
