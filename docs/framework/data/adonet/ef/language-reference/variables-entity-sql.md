---
title: Variables (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 5be9c80c2fce877f179d79f6b2c22f11e31e65a0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248687"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="9d9c4-102">Variables (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9d9c4-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="9d9c4-103">Variable</span><span class="sxs-lookup"><span data-stu-id="9d9c4-103">Variable</span></span>  
 <span data-ttu-id="9d9c4-104">Une expression de variable est une référence à une expression nommée dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="9d9c4-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="9d9c4-105">Une référence de variable doit être un [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identificateur valide, tel que défini dans [identificateurs](identifiers-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9d9c4-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="9d9c4-106">L'exemple suivant montre l'utilisation d'une variable dans l'expression.</span><span class="sxs-lookup"><span data-stu-id="9d9c4-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="9d9c4-107">Le `c` dans la clause FROM représente la définition de la variable.</span><span class="sxs-lookup"><span data-stu-id="9d9c4-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="9d9c4-108">Le `c` dans la clause SELECT représente la référence à la variable.</span><span class="sxs-lookup"><span data-stu-id="9d9c4-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```  
select c   
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d9c4-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d9c4-109">See also</span></span>

- [<span data-ttu-id="9d9c4-110">Identificateurs</span><span class="sxs-lookup"><span data-stu-id="9d9c4-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="9d9c4-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d9c4-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="9d9c4-112">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9d9c4-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
