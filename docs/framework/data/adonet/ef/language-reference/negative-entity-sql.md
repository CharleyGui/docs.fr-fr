---
title: '- Encadré (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: 7716b9115587a873531be9c14b7da93c7a148ed8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319538"
---
# <a name="--negative-entity-sql"></a>- (négatif) (Entity SQL)
Retourne la forme négative de la valeur d'une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Toute expression valide de l'un des types de données numériques.  
  
## <a name="result-types"></a>Types de résultats  
 Type de données de l' `expression`.  
  
## <a name="remarks"></a>Notes  
 Si l' `expression` est un type non signé, le type du résultat sera le type signé le plus proche du type de l' `expression`. Par exemple, si l' `expression` est de type Byte, une valeur de type Int16 sera retournée.  
  
## <a name="example"></a>Exemple  
 La requête Entity SQL ci-dessous utilise l'opérateur arithmétique - pour retourner la forme négative de la valeur d'une expression numérique. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
