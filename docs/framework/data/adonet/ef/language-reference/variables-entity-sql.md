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
# <a name="variables-entity-sql"></a><span data-ttu-id="2b3b5-102">Variables (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2b3b5-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="2b3b5-103">Variable</span><span class="sxs-lookup"><span data-stu-id="2b3b5-103">Variable</span></span>  
 <span data-ttu-id="2b3b5-104">Une expression de variable est une référence à une expression nommée dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="2b3b5-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="2b3b5-105">Une référence de variable doit être un identificateur [!INCLUDE[esql](../../../../../../includes/esql-md.md)] valide, tel que défini dans [identificateurs](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2b3b5-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="2b3b5-106">L'exemple suivant montre l'utilisation d'une variable dans l'expression.</span><span class="sxs-lookup"><span data-stu-id="2b3b5-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="2b3b5-107">Le `c` dans la clause FROM représente la définition de la variable.</span><span class="sxs-lookup"><span data-stu-id="2b3b5-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="2b3b5-108">Le `c` dans la clause SELECT représente la référence à la variable.</span><span class="sxs-lookup"><span data-stu-id="2b3b5-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b3b5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b3b5-109">See also</span></span>

- [<span data-ttu-id="2b3b5-110">Identificateurs</span><span class="sxs-lookup"><span data-stu-id="2b3b5-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="2b3b5-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2b3b5-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="2b3b5-112">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2b3b5-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
