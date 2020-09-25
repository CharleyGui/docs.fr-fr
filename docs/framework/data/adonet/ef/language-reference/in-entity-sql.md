---
title: IN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: 582a3b988247f1484197c0905fecf7f4407f88b0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203668"
---
# <a name="in-entity-sql"></a>IN (Entity SQL)

Détermine si une valeur correspond à une valeur incluse dans une collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a>Arguments  

 `value`  
 Toute expression valide qui retourne la valeur dont rechercher une correspondance.  
  
 [ NOT ]  
 Spécifie que la valeur du résultat `Boolean` de IN est inversée.  
  
 `expression`  
 Toute expression valide qui retourne la collection dans laquelle rechercher une correspondance. Toutes les expressions doivent être du même type que le `value`ou d'un type de base commun ou dérivé de celui-ci.  
  
## <a name="return-value"></a>Valeur renvoyée  

 `true` si la valeur est trouvée dans la collection ; null si la valeur ou la collection est Null ; sinon, `false`. L'utilisation de NOT IN inverse les résultats de IN.  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL ci-dessous utilise l'opérateur IN pour déterminer si une valeur correspond à une valeur contenue dans une collection. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
