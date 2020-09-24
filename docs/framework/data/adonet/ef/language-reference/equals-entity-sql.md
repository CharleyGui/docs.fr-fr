---
title: = (égal à) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: 31299670d9f47ed7672b980a3415b8d214463b8e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148085"
---
# <a name="-equals-entity-sql"></a>= (égal à) (Entity SQL)

Compare l'égalité de deux expressions.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression = expression  
-- or
expression == expression  
```  
  
## <a name="arguments"></a>Arguments  

 `expression`  
 Toute expression valide. Les deux expressions doivent avoir des types de données implicitement convertibles.  
  
## <a name="result-types"></a>Types des résultats  

 `true` si l'expression de gauche est égale à l'expression de droite ; sinon, `false`.  
  
## <a name="remarks"></a>Notes  

 L'opérateur « = = » est équivalent à « = ».  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL ci-dessous utilise l'opérateur de comparaison « = » pour comparer l'égalité de deux expressions. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#equals)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
