---
title: SET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 2ac7db5b22ad21eb152788b6c6d6a8e65c1f6a7b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169633"
---
# <a name="set-entity-sql"></a>SET (Entity SQL)

L'expression SET est utilisée pour convertir une collection d'objets en ensemble grâce à la production d'une nouvelle collection dans laquelle toutes les éléments en double ont été supprimés.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
SET ( expression )  
```  
  
## <a name="arguments"></a>Arguments  

 `expression`  
 Toute expression de requête valide qui retourne une collection.  
  
## <a name="remarks"></a>Notes  

 L'expression d'ensemble `SET(c)` est logiquement équivalente à l'instruction select suivante :  
  
```sql  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET` est l'un des opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] . Tous les opérateurs de jeu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sont évalués de gauche à droite. Pour plus d’informations sur les opérateurs de jeu [, consultez except](except-entity-sql.md) [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL ci-dessous utilise l'expression SET pour convertir une collection d'objets en ensemble. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#SET](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#set)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
