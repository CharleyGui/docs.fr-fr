---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 10c5ecb2b44c85dccd758cc1cf63a152da045cc1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251078"
---
# <a name="deref-entity-sql"></a>DEREF (Entity SQL)
Déréférence une valeur de référence et génère le résultat de ce déréférencement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression de requête valide qui retourne une collection.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur de l'entité référencée.  
  
## <a name="remarks"></a>Notes  
 L'opérateur DEREF déréférence une valeur de référence et génère le résultat de ce déréférencement. Par exemple, si `r` est une référence de type Ref\<T >, `Deref(r)` est une expression de type `T` qui génère l’entité référencée par `r`. Si la valeur de référence est null ou non résolue (autrement dit, la cible de la référence n'existe pas), le résultat de l'opérateur DEREF est null.  
  
## <a name="example"></a>Exemples  
 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur DEREF pour déréférencer une valeur de référence et générer le résultat de ce déréférencement. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-primitivetype-results.md)de PrimitiveType.  
  
2. Passez à la méthode ExecutePrimitiveTypeQuery la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [REF](ref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [KEY](key-entity-sql.md)
- [Types structurés autorisant la valeur null](nullable-structured-types-entity-sql.md)
