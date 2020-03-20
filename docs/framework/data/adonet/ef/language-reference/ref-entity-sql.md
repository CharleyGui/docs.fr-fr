---
title: REF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 40a5afd7eb99dba7cae8fe14ed0a45213fda94a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149945"
---
# <a name="ref-entity-sql"></a>REF (Entity SQL)
Retourne une référence à une instance d'entité.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
REF( expression )
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression valide qui produit une instance d'un type d'entité.  
  
## <a name="return-value"></a>Valeur de retour  
 Référence à l'instance d'entité spécifiée.  
  
## <a name="remarks"></a>Notes   
 Une référence d'entité se compose de la clé d'entité et d'un nom de jeu d'entités. Des jeux d'entités différents pouvant être basés sur le même type d'entité, une clé d'entité particulière peut apparaître dans plusieurs jeux d'entités. Toutefois, une référence d'entité est toujours unique. Si l'expression d'entrée représente une entité rendue persistante, une référence à cette entité est retournée. Si l'expression d'entrée n'est pas une entité rendue persistante, une référence Null à cette entité est retournée.  
  
 Si l'opérateur d'extraction de propriété (.) est utilisé pour accéder à une propriété d'une entité, la référence est automatiquement supprimée.  
  
## <a name="example"></a> Exemple  
 La requête Entity SQL suivante utilise l'opérateur REF pour retourner la référence d'un argument d'entité d'entrée. La même requête supprime la référence car nous utilisons une opération d'extraction de propriété (.) pour accéder à une propriété de l'entité Product. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure dans [Comment: Exécuter une requête qui retourne primitiveType Résultats](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a>Voir aussi

- [DEREF](deref-entity-sql.md)
- [CREATEREF](createref-entity-sql.md)
- [Clé](key-entity-sql.md)
- [Référence Entity SQL](entity-sql-reference.md)
- [Définitions de types](type-definitions-entity-sql.md)
