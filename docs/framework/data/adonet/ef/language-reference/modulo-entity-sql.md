---
title: (Modulo) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: a30306539d45c3718d2e948e9717997bbe2104fa
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250085"
---
# <a name="modulo-entity-sql"></a>(Modulo) (Entity SQL)
Retourne le reste d'une expression divisée par une autre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Arguments  
 `dividend`  
 Expression numérique à diviser. `dividend` correspond à toute expression valide de l'un des types de données numériques.  
  
 `divisor`  
 Expression numérique par laquelle diviser le dividende. `divisor` correspond à toute expression valide de l'un des types de données numériques.  
  
## <a name="result-types"></a>Types de résultats  
 Edm.Int32  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL ci-dessous utilise l'opérateur arithmétique % pour retourner le reste d'une expression divisée par une autre. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
