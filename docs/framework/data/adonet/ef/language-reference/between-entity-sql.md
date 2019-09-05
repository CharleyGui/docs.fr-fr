---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 41036e629837bd5861368df545bed9423eac5b23
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251294"
---
# <a name="between-entity-sql"></a>BETWEEN (Entity SQL)
Détermine si une expression a pour résultat une valeur contenue dans une plage spécifiée. L' [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression between a les mêmes fonctionnalités que Transact-SQL entre les expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression valide à tester dans la plage définie par `begin_expression` et `end_expression`. `expression` doit être du même type qu'`begin_expression` et `end_expression`.  
  
 `begin_expression`  
 Toute expression valide. `begin_expression` doit être du même type qu'`expression` et `end_expression`. `begin_expression` doit être inférieur à `end_expression` ou la valeur de retour sera niée.  
  
 `end_expression`  
 Toute expression valide. `end_expression` doit être du même type qu'`expression` et `begin_expression`.  
  
 NOT  
 Indique que le résultat de BETWEEN est inversé.  
  
 AND  
 Espace réservé qui indique que `expression` doit se trouver dans la plage définie par `begin_expression` et `end_expression`.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` si `expression` est entre la plage indiquée par `begin_expression` et `end_expression` ; sinon, `false`. La valeur `null` est retournée si `expression` a la valeur `null` ou si `begin_expression` ou `end_expression` a la valeur `null`.  
  
## <a name="remarks"></a>Notes  
 Pour spécifier une plage exclusive, utilisez les opérateurs « supérieur à » (>) et « inférieur à » (<) au lieu de BETWEEN.  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL ci-dessous utilise l'opérateur BETWEEN pour déterminer si une expression génère une valeur située dans une plage spécifiée. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
