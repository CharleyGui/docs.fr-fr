---
title: Variables (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: bb8e6ebe81dacc7ec0f45fdde65b9c18cfd76789
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319198"
---
# <a name="variables-entity-sql"></a>Variables (Entity SQL)
## <a name="variable"></a>Variable  
 Une expression de variable est une référence à une expression nommée dans la portée actuelle. Une référence de variable doit être un identificateur [!INCLUDE[esql](../../../../../../includes/esql-md.md)] valide, tel que défini dans [identificateurs](identifiers-entity-sql.md).  
  
 L'exemple suivant montre l'utilisation d'une variable dans l'expression. Le `c` dans la clause FROM représente la définition de la variable. Le `c` dans la clause SELECT représente la référence à la variable.  
  
```sql  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a>Voir aussi

- [Identificateurs](identifiers-entity-sql.md)
- [Paramètres](parameters-entity-sql.md)
- [Vue d’ensemble d’Entity SQL](entity-sql-overview.md)
