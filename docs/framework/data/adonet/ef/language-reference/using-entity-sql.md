---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: bdab81ed8acae5e757de0a669922dc79d0303ee4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203590"
---
# <a name="using-entity-sql"></a>USING (Entity SQL)

Spécifie les espaces de noms utilisés dans une expression de requête.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a>Arguments  

 `alias`  
 Spécifie un alias plus court avec lequel qualifier un espace de noms.  
  
 `namespace`  
 Tout espace de noms valide.  
  
## <a name="example"></a>Exemple  

 La requête Entity SQL ci-dessous utilise l'opérateur USING pour spécifier les espaces de noms utilisés dans une expression de requête. Pour compiler et exécuter cette requête, procédez comme suit :  
  
1. Suivez la procédure décrite dans [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a>Voir aussi

- [Espaces de noms](namespaces-entity-sql.md)
- [Référence Entity SQL](entity-sql-reference.md)
