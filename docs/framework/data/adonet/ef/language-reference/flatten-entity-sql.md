---
title: FLATTEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1a670c63-0a29-4738-80e6-101f66af05c3
ms.openlocfilehash: 36ae2b2b1264150bc66d09366ee33723ed7b28a8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166701"
---
# <a name="flatten-entity-sql"></a>FLATTEN (Entity SQL)

Convertit une collection de collections en collection plane. La nouvelle collection contient les mêmes éléments que l'ancienne, mais sans structure imbriquée.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
FLATTEN ( collection )  
```  
  
## <a name="arguments"></a>Arguments  

 `collection`  
 Expression valide qui retourne une collection de collections de valeurs à aplanir en une seule.  
  
## <a name="remarks"></a>Notes  

 `FLATTEN` est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite. Pour plus d’informations sur les opérateurs de jeu [, consultez except](except-entity-sql.md) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL ci-dessous utilise l'opérateur `FLATTEN` pour convertir une collection de collections en collection plane. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#FLATTEN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#flatten)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
