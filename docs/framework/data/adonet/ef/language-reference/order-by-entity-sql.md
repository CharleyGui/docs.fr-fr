---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 1233971b172079aa48227d0ec520068afbdf0952
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150067"
---
# <a name="order-by-entity-sql"></a>ORDER BY (Entity SQL)
Spécifie l'ordre de classement utilisé sur les objets retournés dans une instruction SELECT.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
[ ORDER BY
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]
]  
```  
  
## <a name="arguments"></a>Arguments  
 `order_by_expression`  
 Toute expression de requête valide qui spécifie une propriété sur laquelle doit porter le tri. Vous pouvez spécifier plusieurs expressions de classement. L'ordre des expressions de classement dans la clause ORDER BY détermine l'organisation de l'ensemble de résultats trié.  
  
 COLLATE {collation_name}  
 Indique que l'opération ORDER BY doit être effectuée en fonction du classement spécifié dans `collation_name`. COLLATE ne peut s'appliquer qu'aux expressions de chaîne.  
  
 ASC  
 Indique que les valeurs de la propriété spécifiée doivent être triées dans l'ordre croissant, de la plus petite à la plus grande. Il s’agit de la valeur par défaut.  
  
 DESC  
 Indique que les valeurs de la propriété spécifiée doivent être triées dans l'ordre décroissant, de la plus grande à la plus petite.  
  
 LIMIT `n`  
 Seuls les `n` premiers éléments sont sélectionnés.  
  
 SKIP `n`  
 Ignore les `n` premiers éléments.  
  
## <a name="remarks"></a>Notes   
 La clause ORDER BY est logiquement appliquée au résultat de la clause SELECT. La clause ORDER BY peut faire référence aux éléments de la liste de sélection avec leurs alias. La clause ORDER BY peut également faire référence à d'autres variables qui se trouvent actuellement dans l'étendue. Toutefois, si la clause SELECT a été spécifiée avec un modificateur DISTINCT, la clause ORDER BY ne peut faire référence qu'à des alias de la clause SELECT.  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 Chaque expression contenue dans la clause ORDER BY doit correspondre à un type pouvant être comparé en inégalité (inférieur à ou supérieur à, etc.). Ces types sont généralement des primitives scalaires telles que des nombres, des chaînes et des dates. Les RowTypes de type comparable peuvent également être comparés sur le plan de l'ordre de classement.  
  
 Si votre code effectue une itération sur un ensemble ordonné autre qu'une projection de niveau supérieur, il n'est pas garanti que le résultat conservera son ordre de classement.  

Dans l’échantillon suivant, l’ordre est garanti pour être conservé :

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

Dans la requête suivante, la commande de la requête imbriquée est ignorée :  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 Pour une opération UNION, UNION ALL, EXCEPT ou INTERSECT triée, utilisez le modèle suivant :  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a>Mots clés restreints  
 Les mots clés suivants doivent être mis entre guillemets lorsqu'ils sont utilisés dans une clause `ORDER BY` :  
  
- CROSS  
  
- FULL  
  
- KEY  
  
- LEFT  
  
- ORDER  
  
- OUTER  
  
- RIGHT  
  
- ROW  
  
- VALEUR  
  
## <a name="ordering-nested-queries"></a>Ordre de tri des requêtes imbriquées  
 Dans Entity Framework, une expression imbriquée peut être placée n'importe où dans la requête ; l'ordre d'une requête imbriquée n'est pas conservé.  

La requête suivante commandera les résultats par le nom de famille :  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

Dans la requête suivante, la commande de la requête imbriquée est ignorée :  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a> Exemple  
 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur ORDER BY pour spécifier l'ordre de tri employé sur les objets retournés dans une instruction SELECT. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a>Voir aussi

- [Expressions de requête](query-expressions-entity-sql.md)
- [Référence Entity SQL](entity-sql-reference.md)
- [PASSER](skip-entity-sql.md)
- [Limite](limit-entity-sql.md)
- [Retour au début](top-entity-sql.md)
