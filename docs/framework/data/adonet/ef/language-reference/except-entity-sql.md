---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: d00fdeed01de80e441d28e2bcd5da084571b0361
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251043"
---
# <a name="except-entity-sql"></a>EXCEPT (Entity SQL)
Retourne une collection de valeurs distinctes à partir de l'expression de requête située du côté gauche de l'opérande EXCEPT, qui ne sont pas retournées à partir de l'expression de requête située à droite de l'opérande EXCEPT. Toutes les expressions doivent être du même type que le `expression`ou d'un type de base commun ou dérivé de celui-ci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression de requête valide qui retourne une collection à comparer avec la collection retournée par une autre expression de requête.  
  
## <a name="return-value"></a>Valeur de retour  
 Collection du même type que l' `expression`ou d'un type de base commun ou dérivé de celui-ci.  
  
## <a name="remarks"></a>Notes  
 EXCEPT est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite. Le tableau ci-dessous présente la priorité des opérateurs Set [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
|Priorité|Opérateurs|  
|----------------|---------------|  
|Maximale|INTERSECT|  
||UNION<br /><br /> UNION ALL|  
||EXCEPT|  
|Minimale|EXISTS<br /><br /> OVERLAPS<br /><br /> FLATTEN<br /><br /> SET|  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL ci-dessous utilise l'opérateur EXCEPT pour retourner une collection de valeurs distinctes provenant de deux expressions de requête. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
