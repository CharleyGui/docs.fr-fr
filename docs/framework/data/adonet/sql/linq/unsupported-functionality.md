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
# <a name="unsupported-functionality"></a><span data-ttu-id="b6738-102">Fonctionnalités non prises en charge</span><span class="sxs-lookup"><span data-stu-id="b6738-102">Unsupported Functionality</span></span>

<span data-ttu-id="b6738-103">Dans LINQ to SQL, les fonctionnalités SQL suivantes ne peuvent pas être exposées via la traduction de constructions du Common Language Runtime (CLR) et .NET Framework existantes :</span><span class="sxs-lookup"><span data-stu-id="b6738-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
- `STDDEV`  
  
- `LIKE`  
  
     <span data-ttu-id="b6738-104">Bien que `LIKE` ne soit pas prise en charge par le biais de la traduction directe, il existe des fonctionnalités similaires dans la classe <xref:System.Data.Linq.SqlClient.SqlMethods>.</span><span class="sxs-lookup"><span data-stu-id="b6738-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="b6738-105">Pour plus d'informations, consultez <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b6738-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
- `DATEDIFF`  
  
     <span data-ttu-id="b6738-106">LINQ to SQL a une prise en charge limitée de `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="b6738-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="b6738-107">Il existe des fonctionnalités similaires dans la classe <xref:System.Data.Linq.SqlClient.SqlMethods>.</span><span class="sxs-lookup"><span data-stu-id="b6738-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
- `ROUND`  
  
     <span data-ttu-id="b6738-108">LINQ to SQL a une prise en charge limitée de `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="b6738-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="b6738-109">Pour plus d’informations, consultez [méthodes System. Math](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b6738-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6738-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6738-110">See also</span></span>

- [<span data-ttu-id="b6738-111">Fonctions et types de données</span><span class="sxs-lookup"><span data-stu-id="b6738-111">Data Types and Functions</span></span>](data-types-and-functions.md)
