---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: c0c975ab5cf2761496db6efa1f88f409aa1b1abd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148215"
---
# <a name="deref-entity-sql"></a>DEREF (Entity SQL)

Déréférence une valeur de référence et génère le résultat de ce déréférencement.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a>Arguments  

 `expression`  
 Toute expression de requête valide qui retourne une collection.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Valeur de l'entité référencée.  
  
## <a name="remarks"></a>Notes  

 L'opérateur DEREF déréférence une valeur de référence et génère le résultat de ce déréférencement. Par exemple, si `r` est une référence de type Ref \<T> , `Deref(r)` est une expression de type `T` qui génère l’entité référencée par `r` . Si la valeur de référence est null ou non résolue (autrement dit, la cible de la référence n'existe pas), le résultat de l'opérateur DEREF est null.  
  
## <a name="example"></a>Exemple  

 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur DEREF pour déréférencer une valeur de référence et générer le résultat de ce déréférencement. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Passez à la méthode ExecutePrimitiveTypeQuery la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Réf](ref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [Types structurés Nullable](nullable-structured-types-entity-sql.md)
