---
title: OVERLAPS (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 41743e89-79cb-4d7b-8a27-355b45024b61
ms.openlocfilehash: fef90beebf1c2723c767eaf5155542ad40d5fcb8
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249733"
---
# <a name="overlaps-entity-sql"></a>OVERLAPS (Entity SQL)
Détermine si deux collections ont des éléments en commun.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression OVERLAPS expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression de requête valide qui retourne une collection à comparer avec la collection retournée par une autre expression de requête. Toutes les expressions doivent être du même type que le `expression`ou d'un type de base commun ou dérivé de celui-ci.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` si les deux collections ont des éléments en commun ; sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Les chevauchements offrent des fonctionnalités équivalentes à celles-ci :  
  
 `EXISTS ( expression INTERSECT expression )`  
  
 OVERLAPS est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite. Pour obtenir des informations de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] précédence pour les opérateurs de jeu, consultez [except](except-entity-sql.md).  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL ci-dessous utilise l'opérateur OVERLAPS pour déterminer si deux collections ont une valeur commune. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#OVERLAPS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#overlaps)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
