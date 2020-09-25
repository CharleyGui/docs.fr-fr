---
title: '&amp;&amp; LES (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
ms.openlocfilehash: 86ff43f8ed20c5696d15e21284394c3cb63200e3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198039"
---
# <a name="ampamp-and-entity-sql"></a>&amp;&amp; LES (Entity SQL)

Retourne `true` si les deux expressions ont pour valeur `true`; sinon, `false` ou la valeur `NULL`.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
boolean_expression AND boolean_expression
```

or  

```csharp
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a>Arguments  

 `boolean_expression`  
 Toute expression valide qui retourne une valeur booléenne.  
  
## <a name="remarks"></a>Notes  

 Les doubles « et » commerciaux (&&) ont la même fonctionnalité que l'opérateur AND.  
  
 Le tableau ci-dessous indique les valeurs d'entrée et les types de retour possibles.  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|TRUE|FALSE|NULL|  
|`FALSE`|false|FALSE|FALSE|  
|`NULL`|NULL|FALSE|NULL|  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL ci-dessous montre comment utiliser l'opérateur AND. Cette requête est basée sur le modèle de vente AdventureWorks Sales Model. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2. Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
