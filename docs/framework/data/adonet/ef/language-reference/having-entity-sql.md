---
title: HAVING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
ms.openlocfilehash: 76a63140668fb1f41cf9e6f901d9a43240a1d098
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936083"
---
# <a name="having-entity-sql"></a>HAVING (Entity SQL)
Spécifie une condition de recherche pour un groupe ou un agrégat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ HAVING search_condition ]  
```  
  
## <a name="arguments"></a>Arguments  
 `search_condition`  
 Indique les critères de recherche à réunir pour le groupe ou l'agrégat. Lorsque HAVING est utilisé avec GROUP BY ALL, la clause HAVING remplace ALL.  
  
## <a name="remarks"></a>Notes  
 La clause HAVING est utilisée pour spécifier une condition de filtrage supplémentaire sur le résultat d'un regroupement. Si aucune clause GROUP BY n'est spécifiée dans l'expression de requête, un groupe implicite constitué d'un seul ensemble est supposé exister.  
  
> [!NOTE]
> HAVING ne peut être utilisé qu’avec l’instruction [Select](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) . Lorsque [Group by](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) n’est pas utilisé, having se comporte comme une clause WHERE.  
  
 La clause HAVING fonctionne comme la clause WHERE, à la différence près que son application intervient après l'opération GROUP BY. Cela signifie que la clause HAVING ne peut faire référence qu'à des agrégats et des alias de regroupement, comme l'illustre l'exemple suivant.  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 La clause précédente limite les groupes à ceux qui comportent plusieurs produits.  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL ci-dessous utilise les opérateurs HAVING et GROUP BY pour spécifier un critère de recherche pour un groupe ou un agrégat. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite [dans la rubrique Procédure: Exécutez une requête qui retourne les résultats](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)de PrimitiveType.  
  
2. Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Expressions de requête](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
