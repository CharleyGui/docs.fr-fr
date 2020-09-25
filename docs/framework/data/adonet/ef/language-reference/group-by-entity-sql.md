---
title: GROUP BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cf4f4972-4724-4945-ba44-943a08549139
ms.openlocfilehash: 281d5d2df389f0952f0552747fa12b67b14d470c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204487"
---
# <a name="group-by-entity-sql"></a>GROUP BY (Entity SQL)

Indique les groupes dans lesquels doivent être placés les objets retournés par une expression de requête ([SELECT](select-entity-sql.md)).  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
[ GROUP BY aliasedExpression [ ,...n ] ]  
```  
  
## <a name="arguments"></a>Arguments  

 `aliasedExpression`  
 Toute expression de requête valide sur laquelle le regroupement est effectué. `expression` peut être une propriété ou une expression non agrégée qui référence une propriété retournée par la clause FROM. Chaque expression contenue dans une clause GROUP BY doit être évaluée à un type pouvant être comparé en égalité. Ces types sont généralement des primitives scalaires telles que des nombres, des chaînes et des dates. Vous ne pouvez pas effectuer de regroupement sur une collection.  
  
## <a name="remarks"></a>Notes  

 Si les fonctions d’agrégation sont incluses dans la clause SELECT \<select list> , Group by calcule une valeur de synthèse pour chaque groupe. Lorsque la clause GROUP BY est spécifiée, vous devez inclure dans la liste GROUP BY chaque nom de propriété des expressions de non-agrégation figurant dans la liste de sélection, ou l'expression GROUP BY doit correspondre exactement à l'expression figurant dans la liste de sélection.  
  
> [!NOTE]
> Si la clause ORDER BY n'est pas spécifiée, les groupes retournés par la clause GROUP BY ne sont pas triés dans un ordre particulier. Nous vous recommandons de toujours utiliser la clause ORDER BY pour définir un ordre de classement des données particulier.  
  
 Lorsqu'une clause GROUP BY est spécifiée, explicitement ou implicitement (par exemple, par une clause HAVING dans la requête), l'étendue actuelle est masquée, et une nouvelle étendue est introduite.  
  
 La clause SELECT, la clause HAVING et la clause ORDER BY ne pourront plus faire référence aux noms d'élément spécifiés dans la clause FROM. Vous ne pouvez faire référence qu'aux expressions de regroupement proprement dites. Pour ce faire, vous pouvez attribuer de nouveaux noms (alias) à chaque expression de regroupement. Si aucun alias n'est spécifié pour une expression de regroupement, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] essaie d'en générer un en utilisant les règles de génération d'alias, comme l'illustre l'exemple suivant.  
  
 `SELECT g1, g2, ...gn FROM c as c1`  
  
 `GROUP BY e1 as g1, e2 as g2, ...en as gn`  
  
 Les expressions contenues dans la clause GROUP BY ne peuvent pas faire référence aux noms définis précédemment dans cette même clause GROUP BY.  
  
 En plus de regrouper des noms, vous pouvez également spécifier des agrégats dans la clause SELECT, la clause HAVING et la clause ORDER BY. Un agrégat contient une expression évaluée pour chaque élément du groupe. L'opérateur d'agrégation réduit les valeurs de toutes ces expressions (généralement, mais pas systématiquement, à une valeur unique). L'expression d'agrégation peut afficher dans l'étendue parente les références aux noms d'élément d'origine ou aux nouveaux noms introduits par la clause GROUP BY elle-même. Bien que les agrégats apparaissent dans les clauses SELECT, HAVING et ORDER BY, ils sont en réalité évalués d'après la même étendue en tant qu'expressions de regroupement, comme l'illustre l'exemple suivant.  
  
 `SELECT name, sum(o.Price * o.Quantity) as total`  
  
 `FROM orderLines as o`  
  
 `GROUP BY o.Product as name`  
  
 Cette requête utilise la clause GROUP BY pour générer un rapport sur le coût de tous les produits commandés, réparti par produit. Elle attribue le nom `name` au produit dans le cadre de l'expression de regroupement, puis référence ce nom dans la liste SELECT. Elle spécifie également l'agrégat `sum` dans la liste SELECT qui référence en interne le prix et la quantité de la ligne de commande.  
  
 Chaque expression clé GROUP BY doit comporter au moins une référence à l'étendue d'entrée :  
  
```sql  
SELECT FROM Persons as P  
GROUP BY Q + P   -- GOOD  
GROUP BY Q   -- BAD  
GROUP BY 1   -- BAD, a constant is not allowed  
```  
  
 Pour obtenir un exemple d’utilisation de GROUP BY, consultez [HAVING](having-entity-sql.md).  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL suivante utilise l'opérateur GROUP BY pour spécifier les groupes dans lesquels les objets sont retournés par une requête. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#GROUPBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#groupby)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Expressions de requête](query-expressions-entity-sql.md)
