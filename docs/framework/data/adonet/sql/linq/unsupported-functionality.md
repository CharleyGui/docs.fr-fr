---
title: Fonctionnalités non prises en charge
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: d4fe3d91b80197d962989cd2d3bc9bb2df6e3ffe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164153"
---
# <a name="unsupported-functionality"></a>Fonctionnalités non prises en charge

Dans LINQ to SQL, les fonctionnalités SQL suivantes ne peuvent pas être exposées via la traduction de constructions du Common Language Runtime (CLR) et .NET Framework existantes :  
  
- `STDDEV`  
  
- `LIKE`  
  
     Bien que `LIKE` ne soit pas prise en charge par le biais de la traduction directe, il existe des fonctionnalités similaires dans la classe <xref:System.Data.Linq.SqlClient.SqlMethods>. Pour plus d'informations, consultez <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.  
  
- `DATEDIFF`  
  
     LINQ to SQL a une prise en charge limitée de `DATEDIFF`. Il existe des fonctionnalités similaires dans la classe <xref:System.Data.Linq.SqlClient.SqlMethods>.  
  
- `ROUND`  
  
     LINQ to SQL a une prise en charge limitée de `ROUND`. Pour plus d’informations, consultez [méthodes System. Math](system-math-methods.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions et types de données](data-types-and-functions.md)
