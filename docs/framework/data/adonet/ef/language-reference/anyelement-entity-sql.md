---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: e060956545ca924fa6fedb80b2f53ff312f307a2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201198"
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (Entity SQL)

Extrait un élément d'une collection à valeurs multiples.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>Arguments  

 `expression`  
 Toute expression de requête valide qui retourne une collection dont extraire un élément.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Élément unique de la collection ou élément arbitraire si la collection en comporte plusieurs ; si la collection est vide, retourne `null`. Si `collection` est une collection de type `Collection<T>` , `ANYELEMENT(collection)` est une expression valide qui produit une instance de type `T` .  
  
## <a name="remarks"></a>Notes  

 ANYELEMENT extrait un élément arbitraire d'une collection à valeurs multiples. L'exemple ci-dessous tente d'extraire un élément singleton du jeu `Customers`.  
  
```csharp
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>Exemple  

 La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur ANYELEMENT pour extraire un élément d'une collection à valeurs multiples. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Types structurés Nullable](nullable-structured-types-entity-sql.md)
