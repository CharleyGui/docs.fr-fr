---
title: Composition de requêtes Entity SQL imbriquées
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 3aa2e53b584eece9cc5e2d26791c78ffe33f9e35
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251147"
---
# <a name="composing-nested-entity-sql-queries"></a>Composition de requêtes Entity SQL imbriquées
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] est un langage fonctionnel riche. Le bloc de construction [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de est une expression. Contrairement au langage SQL [!INCLUDE[esql](../../../../../../includes/esql-md.md)] classique, n’est pas limité à un jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de résultats tabulaire : prend en charge la composition d’expressions complexes qui peuvent avoir des littéraux, des paramètres ou des expressions imbriquées. Une valeur de l’expression peut être paramétrable ou composée d’une autre expression.  
  
## <a name="nested-expressions"></a>Expressions imbriquées  
 Une expression imbriquée peut être placée partout où une valeur du type qu'elle retourne est acceptée. Par exemple :  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 Une requête imbriquée peut être placée dans une clause de projection. Par exemple :  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], les requêtes imbriquées doivent toujours être placées entre parenthèses :  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 L'exemple suivant montre comment imbriquer correctement des expressions dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] : [Guide pratique pour Ordonner l’Union de deux](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))requêtes.  
  
## <a name="nested-queries-in-projection"></a>Requêtes imbriquées dans la projection  
 Les requêtes imbriquées d'une clause de projection peuvent être traduites en requêtes de produit cartésien sur le serveur. Sur certains serveurs principaux dont SQL Server, cela peut avoir pour conséquences l'augmentation de volume de la table TempDB et une diminution des performances du serveur.  
  
 Vous trouverez ci-dessous un exemple de ce type de requête :  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>Ordre de tri des requêtes imbriquées  
 Dans Entity Framework, une expression imbriquée peut être placée n'importe où dans la requête. Entity SQL offrant une grande souplesse dans l'écriture des requêtes, il est possible d'écrire une requête qui contient un classement des requêtes imbriquées. Toutefois, l'ordre d'une requête imbriquée n'est pas conservé.  
  
```  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble d’Entity SQL](entity-sql-overview.md)
