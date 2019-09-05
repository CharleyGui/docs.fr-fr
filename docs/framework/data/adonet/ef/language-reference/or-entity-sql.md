---
title: '|| (OR) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: c88e041638fbe6f32717ce9c4f9c2ff6fb56d803
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249771"
---
# <a name="-or-entity-sql"></a>|| (OR) (Entity SQL)
Combine deux expressions `Boolean` .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  
 `boolean_expression`  
 Toute expression valide qui retourne une valeur `Boolean`.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` si l'une des conditions a la valeur `true`; sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 OR est un opérateur logique [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Il est utilisé pour combiner deux conditions. Lorsque vous utilisez plusieurs opérateurs logiques dans une instruction, les opérateurs OR sont évalués après les opérateurs AND. L'utilisation de parenthèses permet toutefois de modifier l'ordre de traitement.  
  
 Les barres verticales&#124;&#124;doubles () ont la même fonctionnalité que l’opérateur or.  
  
 Le tableau ci-dessous indique les valeurs d'entrée et les types de retour possibles.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|true|TRUE|TRUE|  
|`FALSE`|TRUE|FALSE|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL ci-dessous utilise l'opérateur OR pour combiner deux expressions `Boolean` . Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
