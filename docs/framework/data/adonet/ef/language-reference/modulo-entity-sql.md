---
title: (Modulo) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 25bd34db3a627fa708e1ab9a3f0e237426487bcb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175705"
---
# <a name="modulo-entity-sql"></a>(Modulo) (Entity SQL)

Retourne le reste d'une expression divisée par une autre.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a>Arguments  

 `dividend`  
 Expression numérique à diviser. `dividend` correspond à toute expression valide de l'un des types de données numériques.  
  
 `divisor`  
 Expression numérique par laquelle diviser le dividende. `divisor` correspond à toute expression valide de l'un des types de données numériques.  
  
## <a name="result-types"></a>Types des résultats  

 Edm.Int32  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL ci-dessous utilise l'opérateur arithmétique % pour retourner le reste d'une expression divisée par une autre. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
