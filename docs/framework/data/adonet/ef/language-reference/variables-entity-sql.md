---
title: Variables (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 88ee41bc08711cf84b8b2e273c9ac0f4267d1d34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149815"
---
# <a name="variables-entity-sql"></a>Variables (Entity SQL)
## <a name="variable"></a>Variable  
 Une expression de variable est une référence à une expression nommée dans la portée actuelle. Une référence variable doit [!INCLUDE[esql](../../../../../../includes/esql-md.md)] être un identifiant valide, tel que défini dans [Identifiers](identifiers-entity-sql.md).  
  
 L'exemple suivant montre l'utilisation d'une variable dans l'expression. Le `c` dans la clause FROM représente la définition de la variable. Le `c` dans la clause SELECT représente la référence à la variable.  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Voir aussi

- [Identificateurs](identifiers-entity-sql.md)
- [Paramètres](parameters-entity-sql.md)
- [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)
