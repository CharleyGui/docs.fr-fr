---
title: Paramètres (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 723e40f523f8bb573e0ffcb1863ed0c082ea9d8d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249590"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="8e5c8-102">Paramètres (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8e5c8-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="8e5c8-103">Les paramètres sont des variables qui sont définies en dehors d'[!INCLUDE[esql](../../../../../../includes/esql-md.md)], généralement par le biais d'une API de liaison qui est utilisée par un langage hôte.</span><span class="sxs-lookup"><span data-stu-id="8e5c8-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="8e5c8-104">Chaque paramètre a un nom et un type.</span><span class="sxs-lookup"><span data-stu-id="8e5c8-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="8e5c8-105">Les noms de paramètres sont définis dans des expressions de requête avec le symbole at (@) comme préfixe.</span><span class="sxs-lookup"><span data-stu-id="8e5c8-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="8e5c8-106">Cela lève l'ambiguïté entre ces noms et les noms de propriétés ou autres noms qui sont définis dans la requête.</span><span class="sxs-lookup"><span data-stu-id="8e5c8-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="8e5c8-107">L’API de liaison du langage hôte fournit des API pour les paramètres de liaison.</span><span class="sxs-lookup"><span data-stu-id="8e5c8-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e5c8-108">Exemples</span><span class="sxs-lookup"><span data-stu-id="8e5c8-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e5c8-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e5c8-109">See also</span></span>

- [<span data-ttu-id="8e5c8-110">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8e5c8-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="8e5c8-111">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8e5c8-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
