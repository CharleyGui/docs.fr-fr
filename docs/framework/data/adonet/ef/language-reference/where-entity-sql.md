---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: b551d15d7de2cf07afc7455b7fd0a0faf6436ccf
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319185"
---
# <a name="where-entity-sql"></a>WHERE (Entity SQL)
La clause WHERE est appliquée directement après la clause [from](from-entity-sql.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Type booléen.  
  
## <a name="remarks"></a>Notes  
 La clause WHERE a la même sémantique que celle décrite dans Transact-SQL. Elle restreint le nombre d’objets générés par l’expression de requête en limitant les éléments des collections sources à ceux qui répondent à la condition.  
  
```sql  
select c from cs as c where e  
```  
  
 L'expression `e` doit être de type booléen.  
  
 La clause WHERE est appliquée directement après la clause FROM et avant tout regroupement, classement ou projection éventuel. Tous les noms d'éléments définis dans la clause FROM sont visibles pour l'expression de la clause WHERE.  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Expressions de requête](query-expressions-entity-sql.md)
