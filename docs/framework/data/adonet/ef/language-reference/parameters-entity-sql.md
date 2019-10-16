---
title: Paramètres (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 8fbca4f10a7c2c3dbaffff978a536b87d31a8df4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319429"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="0970c-102">Paramètres (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="0970c-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="0970c-103">Les paramètres sont des variables qui sont définies en dehors d'[!INCLUDE[esql](../../../../../../includes/esql-md.md)], généralement par le biais d'une API de liaison qui est utilisée par un langage hôte.</span><span class="sxs-lookup"><span data-stu-id="0970c-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="0970c-104">Chaque paramètre a un nom et un type.</span><span class="sxs-lookup"><span data-stu-id="0970c-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="0970c-105">Les noms de paramètres sont définis dans des expressions de requête avec le symbole at (@) comme préfixe.</span><span class="sxs-lookup"><span data-stu-id="0970c-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="0970c-106">Cela lève l'ambiguïté entre ces noms et les noms de propriétés ou autres noms qui sont définis dans la requête.</span><span class="sxs-lookup"><span data-stu-id="0970c-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="0970c-107">L’API de liaison du langage hôte fournit des API pour les paramètres de liaison.</span><span class="sxs-lookup"><span data-stu-id="0970c-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0970c-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="0970c-108">Example</span></span>  
  
```sql  
SELECT c   
      FROM LOB.Customers AS c   
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="0970c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0970c-109">See also</span></span>

- [<span data-ttu-id="0970c-110">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0970c-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="0970c-111">Vue d’ensemble d’Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0970c-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
