---
title: CASE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 58b21d3be8e13a0a2204a4fd6d355f734207c509
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150465"
---
# <a name="case-entity-sql"></a>CASE (Entity SQL)
Évalue un ensemble d'expressions `Boolean` pour déterminer le résultat.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
CASE  
     WHEN Boolean_expression THEN result_expression
    [ ...n ]
     [
    ELSE else_result_expression
     ]
END  
```  
  
## <a name="arguments"></a>Arguments  
 `n`  
 Est un espace réservé indiquant que plusieurs clauses WHEN `Boolean_expression` THEN `result_expression` peuvent être utilisées.  
  
 THEN `result_expression`  
 Expression retournée lorsque `Boolean_expression` a la valeur `true`. `result expression` peut être une expression valide quelconque.  
  
 ELSE `else_result_expression`  
 Expression retournée si aucune opération de comparaison ne donne `true`. Si cet argument est omis et qu'aucune opération de comparaison n'a la valeur `true`, CASE retourne la valeur Null. `else_result_expression` peut être une expression valide quelconque. Les types de données de `else_result_expression` et celui de tout argument `result_expression` doivent être identiques ou permettre une conversion implicite.  
  
 WHEN `Boolean_expression`  
 Expression `Boolean` évaluée lorsque le format CASE recherché est utilisé. `Boolean_expression` peut être une expression `Boolean` valide quelconque.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne le type de priorité le plus élevé de l'ensemble des types dans `result_expression` ainsi que la valeur facultative `else_result_expression`.  
  
## <a name="remarks"></a>Notes   
 L’expression [!INCLUDE[esql](../../../../../../includes/esql-md.md)] de cas ressemble à l’expression de cas de Transact-SQL. Vous pouvez utiliser l'expression case pour effectuer une série de tests conditionnels visant à identifier l'expression qui produira le résultat approprié. Cette forme de l'expression case s'applique à une série d'une ou de plusieurs expressions `Boolean` pour déterminer l'expression résultante correcte.  
  
 La fonction CASE évalue `Boolean_expression` pour chaque clause WHEN dans l'ordre spécifié et retourne l'expression `result_expression` de la première expression `Boolean_expression` qui prend la valeur `true`. Les expressions restantes ne sont pas évaluées. Si aucune expression `Boolean_expression` ne prend la valeur `true`, le moteur de base de données retourne l'expression `else_result_expression` si une clause ELSE est spécifiée ou la valeur Null dans le cas contraire.  
  
 Une instruction CASE ne peut pas retourner de multiset.  
  
## <a name="example"></a> Exemple  
 La requête Entity SQL ci-dessous utilise l'expression CASE pour évaluer un ensemble d'expressions `Boolean` afin de déterminer le résultat. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure dans [Comment: Exécuter une requête qui retourne primitiveType Résultats](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a>Voir aussi

- [Puis](then-entity-sql.md)
- [Sélectionnez](select-entity-sql.md)
- [Référence Entity SQL](entity-sql-reference.md)
