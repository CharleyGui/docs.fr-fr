---
title: WHERE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: a8e1061e-0028-4a6f-8f19-b9f48e96c4b8
ms.openlocfilehash: 939d4c0ec2c30bc71b22fb65ab36644e063f97de
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489845"
---
# <a name="where-entity-sql"></a>WHERE (Entity SQL)
La clause WHERE est appliquée directement après le [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md) clause.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ WHERE expression ]  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Type booléen.  
  
## <a name="remarks"></a>Notes  
 La clause WHERE a la même sémantique que celles décrites pour Transact-SQL. Elle restreint le nombre d’objets générés par l’expression de requête en limitant les éléments des collections sources à ceux qui répondent à la condition.  
  
```  
select c from cs as c where e  
```  
  
 L'expression `e` doit être de type booléen.  
  
 La clause WHERE est appliquée directement après la clause FROM et avant tout regroupement, classement ou projection éventuel. Tous les noms d'éléments définis dans la clause FROM sont visibles pour l'expression de la clause WHERE.  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Expressions de requête](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
