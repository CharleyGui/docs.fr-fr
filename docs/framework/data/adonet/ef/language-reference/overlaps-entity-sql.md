---
title: OVERLAPS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: 6902a44af343c37ccb26412738d9f96b28551814
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204422"
---
# <a name="overlaps-entity-sql"></a>OVERLAPS (Entity SQL)

Détermine si deux collections ont des éléments en commun.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>Arguments  

 `expression`  
 Toute expression de requête valide qui retourne une collection à comparer avec la collection retournée par une autre expression de requête. Toutes les expressions doivent être du même type que le `expression`ou d'un type de base commun ou dérivé de celui-ci.  
  
## <a name="return-value"></a>Valeur renvoyée  

 `true` si les deux collections ont des éléments en commun ; sinon, `false`.  
  
## <a name="remarks"></a>Notes  

 Les chevauchements offrent des fonctionnalités équivalentes à celles-ci :  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 OVERLAPS est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite. Pour obtenir des informations de précédence pour les [!INCLUDE[esql](../../../../../../includes/esql-md.md)] opérateurs de jeu, consultez [except](except-entity-sql.md).  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL ci-dessous utilise l'opérateur OVERLAPS pour déterminer si deux collections ont une valeur commune. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#OVERLAPS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#overlaps)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
