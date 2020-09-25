---
title: Comparaisons null
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: 71b7c4d86debe8cf267b1b65e3d176cbc4704e6d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185104"
---
# <a name="null-comparisons"></a>Comparaisons null

Une valeur `null` dans la source de données indique que la valeur est inconnue. Dans LINQ to Entities requêtes, vous pouvez rechercher les valeurs NULL afin que certains calculs ou comparaisons soient effectués uniquement sur les lignes qui contiennent des données valides ou non nulles. Toutefois, la sémantique Null CLR peut différer par rapport à la sémantique Null de la source de données. La plupart des bases de données utilisent une version de logique à trois valeurs pour gérer les comparaisons de valeurs Null. Autrement dit, une comparaison avec une valeur NULL n’est pas évaluée à `true` ou `false` , elle prend la valeur `unknown` . Il s'agit souvent d'une implémentation de valeurs ANSI Null, mais ce n'est pas toujours le cas.  
  
 Par défaut dans SQL Server, la comparaison Null-égale-Null retourne une valeur Null. Dans l’exemple suivant, les lignes où `ShipDate` a la valeur NULL sont exclues du jeu de résultats, et l’instruction Transact-SQL retourne 0 ligne.  
  
```sql  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 C'est très différent de la sémantique Null CLR, où la comparaison Null-égale-Null retourne true.  
  
 La requête LINQ suivante est exprimée dans le CLR, mais elle est exécutée dans la source de données. Étant donné que rien ne garantit que la sémantique CLR sera respectée au niveau de la source de données, le comportement attendu est indéterminé.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Sélecteurs de clé  

 Un *Sélecteur de clé* est une fonction utilisée dans les opérateurs de requête standard pour extraire une clé d’un élément. Dans la fonction du sélecteur de clé, une expression peut être comparée avec une constante. La sémantique Null CLR est exposée si une expression est comparée à une constante Null ou si deux constantes Null sont comparées. La sémantique Null du magasin est exposée si deux colonnes contenant des valeurs Null dans la source de données sont comparées. Les sélecteurs de clé, qui se trouvent dans un grand nombre des opérateurs de requête standard de classement et de regroupement, tels que <xref:System.Linq.Queryable.GroupBy%2A>, sont utilisés pour sélectionner les clés sur lesquelles trier ou regrouper les résultats de la requête.  
  
## <a name="null-property-on-a-null-object"></a>Propriété Null sur un objet Null  

 Dans le Entity Framework, les propriétés d’un objet null sont null. Lorsque vous essayez de référencer une propriété d'un objet Null dans le CLR, vous recevez un objet <xref:System.NullReferenceException>. Lorsqu'une requête LINQ implique une propriété d'un objet Null, cela peut provoquer un comportement incohérent.  
  
 Par exemple, dans la requête suivante, le cast en `NewProduct` est effectué dans la couche de l’arborescence de commandes, ce qui peut rendre Null la propriété `Introduced`. Si la base de données a défini des comparaisons de valeurs Null telles que la comparaison <xref:System.DateTime> ait la valeur true, la ligne sera incluse.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Transmission de collections de valeurs Null aux fonctions d’agrégation  

 Dans LINQ to Entities, lorsque vous transmettez une collection qui prend en charge `IQueryable` à une fonction d’agrégation, les opérations d’agrégation sont effectuées au niveau de la base de données. Il peut y avoir des différences entre les résultats d'une requête qui a été effectuée en mémoire et ceux d'une requête qui a été effectuée dans la base de données. Avec une requête en mémoire, en l'absence de correspondance, la requête retourne zéro. Dans la base de données, la même requête retourne la valeur `null`. Si une `null` valeur est passée à une fonction d’agrégation LINQ, une exception est levée. Pour accepter `null` les valeurs possibles, effectuez un cast des types et des propriétés des types qui reçoivent les résultats de la requête en types valeur Nullable.  
  
## <a name="see-also"></a>Voir aussi

- [Expressions dans les requêtes LINQ to Entities](expressions-in-linq-to-entities-queries.md)
