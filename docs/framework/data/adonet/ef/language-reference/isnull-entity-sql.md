---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: 9066f9fb68ce2c50e9523881cfa0dd930cd0b52e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319728"
---
# <a name="isnull-entity-sql"></a>ISNULL (Entity SQL)
Détermine si une expression de requête a la valeur NULL.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression de requête valide. Ne peut pas être une collection, posséder des membres de collection ou être un type d'enregistrement avec des propriétés de type collection.  
  
 NOT  
 Inverse le résultat EDM.Boolean de l'opérateur IS NULL.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` si `expression` retourne la valeur NULL ; sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Utilisez `IS NULL` pour déterminer si l'élément d'une jointure externe est NULL :  
  
```sql  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 Utilisez `IS NULL` pour déterminer si un membre a une valeur réelle :  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 Le tableau ci-dessous montre le comportement de l'opérateur `IS NULL` sur certains modèles. Toutes les exceptions sont levées côté client avant que le fournisseur soit appelé :  
  
|Motif|Comportement|  
|-------------|--------------|  
|null IS NULL|Retourne `true`.|  
|TREAT (null AS EntityType) IS NULL|Retourne `true`.|  
|TREAT (null AS ComplexType) IS NULL|Génère une erreur.|  
|TREAT (null AS RowType) IS NULL|Génère une erreur.|  
|EntityType IS NULL|Retourne `true` ou la valeur `false`.|  
|ComplexType IS NULL|Génère une erreur.|  
|RowType IS NULL|Génère une erreur.|  
  
## <a name="example"></a>Exemple  
 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivante utilise l’opérateur IS NOT NULL pour déterminer si une expression de requête n’a pas la valeur null. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
