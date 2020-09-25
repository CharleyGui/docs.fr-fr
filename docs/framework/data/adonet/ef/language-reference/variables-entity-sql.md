---
title: Variables (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: af6d586a22f14a04bfc7ec339d0aa8e9ba7c66c7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180996"
---
# <a name="variables-entity-sql"></a>Variables (Entity SQL)

## <a name="variable"></a>Variable  

 Une expression de variable est une référence à une expression nommée dans la portée actuelle. Une référence de variable doit être un [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identificateur valide, tel que défini dans [identificateurs](identifiers-entity-sql.md).  
  
 L'exemple suivant montre l'utilisation d'une variable dans l'expression. Le `c` dans la clause FROM représente la définition de la variable. Le `c` dans la clause SELECT représente la référence à la variable.  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Voir aussi

- [Identificateurs](identifiers-entity-sql.md)
- [Paramètres](parameters-entity-sql.md)
- [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)
