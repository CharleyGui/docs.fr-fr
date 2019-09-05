---
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: cbaea82108dd3debcca972ca15dea248227330ac
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251100"
---
# <a name="createref-entity-sql"></a>CREATEREF (Entity SQL)
Crée les références à une entité dans un jeu d'entités.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 `entityset_identifier`  
 Identificateur de jeu d'entités ; ne correspond pas à un littéral de chaîne.  
  
 `row_typed_expression`  
 Expression typée ligne correspondant aux propriétés de clés du type d'entité.  
  
## <a name="remarks"></a>Notes  
 La structure de`row_typed_expression` doit être équivalente au type de clé de l'entité. Autrement dit, les champs qu'elle contient doivent être identiques en nombre et en types à ceux des clés de l'entité, et ils doivent être disposés dans le même ordre.  
  
 Dans l'exemple ci-dessous, Orders et BadOrders sont des jeux d'entités de type Order, et Id est supposé être l'unique propriété de clé de type Order. Cet exemple montre comment produire une référence à une entité de BadOrders. Notez que la référence peut être non résolue.  Autrement dit, la référence peut ne pas identifier réellement une entité spécifique. Dans ce cas, une opération `DEREF` sur cette référence retourne une valeur NULL.  
  
```  
select CreateRef(LOB.BadOrders, row(o.Id))   
from LOB.Orders as o   
```  
  
## <a name="example"></a>Exemples  
 La requête Entity SQL ci-dessous utilise l'opérateur CREATEREF pour créer des références à une entité contenue dans un jeu d'entités. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#CREATEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#createref)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [DEREF](deref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [REF](ref-entity-sql.md)
