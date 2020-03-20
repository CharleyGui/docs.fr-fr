---
title: Composition de requêtes Entity SQL imbriquées
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 6b2fc9a32fc30d205b9c33257bf98781cfa07499
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150387"
---
# <a name="composing-nested-entity-sql-queries"></a><span data-ttu-id="2405b-102">Composition de requêtes Entity SQL imbriquées</span><span class="sxs-lookup"><span data-stu-id="2405b-102">Composing Nested Entity SQL Queries</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="2405b-103">est un langage fonctionnel riche.</span><span class="sxs-lookup"><span data-stu-id="2405b-103">is a rich functional language.</span></span> <span data-ttu-id="2405b-104">Le bloc [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de construction de est une expression.</span><span class="sxs-lookup"><span data-stu-id="2405b-104">The building block of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is an expression.</span></span> <span data-ttu-id="2405b-105">Contrairement à SQL classique, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ne se limite [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pas à un ensemble de résultats tabulaires : soutient la composition d’expressions complexes qui peuvent avoir des littérales, des paramètres ou des expressions imbriquées.</span><span class="sxs-lookup"><span data-stu-id="2405b-105">Unlike conventional SQL, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is not limited to a tabular result set: [!INCLUDE[esql](../../../../../../includes/esql-md.md)] supports composing complex expressions that can have literals, parameters, or nested expressions.</span></span> <span data-ttu-id="2405b-106">Une valeur de l'expression peut être paramétrée ou composée d'une autre expression.</span><span class="sxs-lookup"><span data-stu-id="2405b-106">A value in the expression can be parameterized or composed of some other expression.</span></span>  
  
## <a name="nested-expressions"></a><span data-ttu-id="2405b-107">Expressions imbriquées</span><span class="sxs-lookup"><span data-stu-id="2405b-107">Nested Expressions</span></span>  
 <span data-ttu-id="2405b-108">Une expression imbriquée peut être placée partout où une valeur du type qu'elle retourne est acceptée.</span><span class="sxs-lookup"><span data-stu-id="2405b-108">A nested expression can be placed anywhere a value of the type it returns is accepted.</span></span> <span data-ttu-id="2405b-109">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2405b-109">For example:</span></span>  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 <span data-ttu-id="2405b-110">Une requête imbriquée peut être placée dans une clause de projection.</span><span class="sxs-lookup"><span data-stu-id="2405b-110">A nested query can be placed in a projection clause.</span></span> <span data-ttu-id="2405b-111">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2405b-111">For example:</span></span>  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 <span data-ttu-id="2405b-112">Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], les requêtes imbriquées doivent toujours être placées entre parenthèses :</span><span class="sxs-lookup"><span data-stu-id="2405b-112">In [!INCLUDE[esql](../../../../../../includes/esql-md.md)], nested queries must always be enclosed in parentheses:</span></span>  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 <span data-ttu-id="2405b-113">L’exemple suivant montre comment bien [!INCLUDE[esql](../../../../../../includes/esql-md.md)]nicher les expressions dans : [Comment : Ordonner l’Union des deux requêtes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2405b-113">The following example demonstrates how to properly nest expressions in [!INCLUDE[esql](../../../../../../includes/esql-md.md)]: [How to: Order the Union of Two Queries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).</span></span>  
  
## <a name="nested-queries-in-projection"></a><span data-ttu-id="2405b-114">Requêtes imbriquées dans la projection</span><span class="sxs-lookup"><span data-stu-id="2405b-114">Nested Queries in Projection</span></span>  
 <span data-ttu-id="2405b-115">Les requêtes imbriquées d'une clause de projection peuvent être traduites en requêtes de produit cartésien sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="2405b-115">Nested queries in the project clause might get translated into Cartesian product queries on the server.</span></span> <span data-ttu-id="2405b-116">Dans certains serveurs backend, y compris SQL Server, cela peut causer la table TempDB pour obtenir très grand, ce qui peut nuire aux performances du serveur.</span><span class="sxs-lookup"><span data-stu-id="2405b-116">In some backend servers, including SQL Server, this can cause the TempDB table to get very large, which can adversely affect server performance.</span></span>  
  
 <span data-ttu-id="2405b-117">Vous trouverez ci-dessous un exemple de ce type de requête :</span><span class="sxs-lookup"><span data-stu-id="2405b-117">The following is an example of such a query:</span></span>  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="2405b-118">Ordre de tri des requêtes imbriquées</span><span class="sxs-lookup"><span data-stu-id="2405b-118">Ordering Nested Queries</span></span>  
 <span data-ttu-id="2405b-119">Dans Entity Framework, une expression imbriquée peut être placée n'importe où dans la requête.</span><span class="sxs-lookup"><span data-stu-id="2405b-119">In the Entity Framework, a nested expression can be placed anywhere in the query.</span></span> <span data-ttu-id="2405b-120">Entity SQL offrant une grande souplesse dans l'écriture des requêtes, il est possible d'écrire une requête qui contient un classement des requêtes imbriquées.</span><span class="sxs-lookup"><span data-stu-id="2405b-120">Because Entity SQL allows great flexibility in writing queries, it is possible to write a query that contains an ordering of nested queries.</span></span> <span data-ttu-id="2405b-121">Toutefois, l'ordre d'une requête imbriquée n'est pas conservé.</span><span class="sxs-lookup"><span data-stu-id="2405b-121">However, the order of a nested query is not preserved.</span></span>  
  
```sql  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a><span data-ttu-id="2405b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2405b-122">See also</span></span>

- [<span data-ttu-id="2405b-123">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2405b-123">Entity SQL Overview</span></span>](entity-sql-overview.md)
