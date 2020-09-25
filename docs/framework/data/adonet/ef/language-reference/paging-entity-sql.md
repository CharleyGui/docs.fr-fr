---
title: Pagination (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 42f685e0b84109f3099b501b2a75e681af1ea1bb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177473"
---
# <a name="paging-entity-sql"></a>Pagination (Entity SQL)

La pagination physique peut être effectuée à l’aide des sous-clauses [Skip](skip-entity-sql.md) et [Limit](limit-entity-sql.md) de la clause [order by](order-by-entity-sql.md) . Pour effectuer une pagination physique de façon déterministe, vous devez utiliser SKIP et LIMIT. Si vous souhaitez uniquement limiter le nombre de lignes dans le résultat de façon non déterministe, vous devez utiliser [Top](top-entity-sql.md). TOP et SKIP/LIMIT s'excluent mutuellement.  
  
## <a name="top-overview"></a>Vue d'ensemble de TOP  

 La clause SELECT peut avoir une sous-clause TOP facultative après le modificateur ALL/DISTINCT facultatif. La sous-clause TOP spécifie que seul le premier ensemble de lignes sera retourné à partir du résultat de la requête. Pour plus d’informations, consultez [Top](top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>Vue d'ensemble de SKIP et de LIMIT  

 SKIP et LIMIT qui font partie de la clause ORDER BY. Si une sous-clause d'expression SKIP est présente dans une clause ORDER BY, les résultats seront triés en fonction de la spécification de classement et le jeu de résultats inclura une ou plusieurs lignes en commençant à la prochaine ligne immédiatement après l'expression SKIP. Par exemple, SKIP 5 ignore les cinq premières lignes et retourne la sixième ligne et les suivantes. Si une sous-clause d'expression LIMIT est présente dans une clause ORDER BY, la requête sera triée en fonction de la spécification de classement et le nombre de lignes obtenu sera limité par l'expression LIMIT. Par exemple, LIMIT 5 limitera le jeu de résultats à cinq instances ou lignes. SKIP et LIMIT ne doivent pas nécessairement être utilisées ensemble ; vous pouvez utiliser uniquement SKIP ou uniquement LIMIT avec la clause ORDER BY. Pour plus d'informations, voir les rubriques suivantes :  
  
- [SAUT](skip-entity-sql.md)  
  
- [SÉPAR](limit-entity-sql.md)  
  
- [ORDER BY](order-by-entity-sql.md)  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
- [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)
- [Procédure : pagination dans les résultats d’une requête](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
