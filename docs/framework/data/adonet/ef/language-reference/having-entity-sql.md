---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 97ed6e06241804bf2f576c910a2235b0cb570bbb
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833733"
---
# <a name="having-entity-sql"></a>HAVING (Entity SQL)
Spécifie une condition de recherche pour un groupe ou un agrégat.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Arguments  
 `search_condition`  
 Spécifie la condition de recherche à satisfaire pour le groupe ou l'agrégat. Lorsque HAVING est utilisé avec GROUP BY ALL, la clause HAVING remplace ALL.  
  
## <a name="remarks"></a>Remarques  
 La clause HAVING est utilisée pour spécifier une condition de filtrage supplémentaire sur le résultat d'un regroupement. Si aucune clause GROUP BY n'est spécifiée dans l'expression de requête, un groupe implicite constitué d'un seul ensemble est supposé exister.  
  
> [!NOTE]
> HAVING ne peut être utilisé qu’avec l’instruction [Select](select-entity-sql.md) . Lorsque [Group by](group-by-entity-sql.md) n’est pas utilisé, having se comporte comme une clause WHERE.  
  
La clause HAVING fonctionne comme la clause WHERE, à la différence près que son application intervient après l'opération GROUP BY. Cela signifie que la clause HAVING ne peut faire référence qu’à des agrégats et des alias de regroupement, comme illustré dans l’exemple suivant :
  
```sql  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 La clause précédente limite les groupes à ceux qui comportent plusieurs produits.  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL ci-dessous utilise les opérateurs HAVING et GROUP BY pour spécifier un critère de recherche pour un groupe ou un agrégat. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#HAVING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#having)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Expressions de requête](query-expressions-entity-sql.md)
