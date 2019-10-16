---
title: KEY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 14c0b5d273b26c71c9c63e8bbbcef863ac95a5f3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319697"
---
# <a name="key-entity-sql"></a>KEY (Entity SQL)
Extrait la clé d'une référence ou d'une expression d'entité.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a>Notes  
 Une clé d'entité contient les valeurs de clés dans l'ordre correct de l'entité ou de la référence d'entité spécifiée. Plusieurs jeux d'entités pouvant être basés sur le même type d'entité, la même clé peut apparaître dans chaque jeu d'entités. Pour obtenir une référence unique, utilisez `REF`. Le type de retour de l'opérateur KEY est un type de ligne qui inclut un champ pour chaque clé de l'entité, dans le même ordre.  
  
 Dans l'exemple suivant, une référence à l'entité BadOrder est passée à l'opérateur Key, lequel retourne la partie clé de cette référence. Dans le cas présent, un type d'enregistrement ayant exactement un champ correspondant à la propriété `Id` .  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL suivante utilise l'opérateur KEY pour extraire la partie clé d'une expression avec référence de type. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [CREATEREF](createref-entity-sql.md)
- [REF](ref-entity-sql.md)
- [DEREF](deref-entity-sql.md)
