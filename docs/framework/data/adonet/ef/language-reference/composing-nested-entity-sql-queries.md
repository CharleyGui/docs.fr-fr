---
title: Composition de requêtes Entity SQL imbriquées
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 0c9a6a99ff49cfa847f4c1e7ea693fbb2611debd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153064"
---
# <a name="composing-nested-entity-sql-queries"></a>Composition de requêtes Entity SQL imbriquées

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] est un langage fonctionnel riche. Le bloc de construction de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] est une expression. Contrairement au langage SQL classique, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] n’est pas limité à un jeu de résultats tabulaire : [!INCLUDE[esql](../../../../../../includes/esql-md.md)] prend en charge la composition d’expressions complexes qui peuvent avoir des littéraux, des paramètres ou des expressions imbriquées. Une valeur de l'expression peut être paramétrée ou composée d'une autre expression.  
  
## <a name="nested-expressions"></a>Expressions imbriquées  

 Une expression imbriquée peut être placée partout où une valeur du type qu'elle retourne est acceptée. Par exemple :  
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 Une requête imbriquée peut être placée dans une clause de projection. Par exemple :  
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], les requêtes imbriquées doivent toujours être placées entre parenthèses :  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 L’exemple suivant montre comment imbriquer correctement des expressions dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] : [procédure : ordonner l’Union de deux requêtes](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100)).  
  
## <a name="nested-queries-in-projection"></a>Requêtes imbriquées dans la projection  

 Les requêtes imbriquées d'une clause de projection peuvent être traduites en requêtes de produit cartésien sur le serveur. Sur certains serveurs principaux, y compris les SQL Server, la table TempDB peut devenir très volumineuse, ce qui peut nuire aux performances du serveur.  
  
 Vous trouverez ci-dessous un exemple de ce type de requête :  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>Ordre de tri des requêtes imbriquées  

 Dans Entity Framework, une expression imbriquée peut être placée n'importe où dans la requête. Entity SQL offrant une grande souplesse dans l'écriture des requêtes, il est possible d'écrire une requête qui contient un classement des requêtes imbriquées. Toutefois, l'ordre d'une requête imbriquée n'est pas conservé.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)
