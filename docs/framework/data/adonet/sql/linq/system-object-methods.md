---
title: System.Object, méthodes
ms.date: 03/30/2017
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
ms.openlocfilehash: d2b96ca9e7bedd0e0438b47698d4b963844c92f3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155638"
---
# <a name="systemobject-methods"></a><span data-ttu-id="85c16-102">System.Object, méthodes</span><span class="sxs-lookup"><span data-stu-id="85c16-102">System.Object Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="85c16-103">prend en charge les <xref:System.Object> méthodes suivantes.</span><span class="sxs-lookup"><span data-stu-id="85c16-103">supports the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.ToString?displayProperty=nameWithType>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="85c16-104">ne prend pas en charge les méthodes <xref:System.Object> suivantes.</span><span class="sxs-lookup"><span data-stu-id="85c16-104">does not support the following <xref:System.Object> methods.</span></span>  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=nameWithType>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=nameWithType>|  
|<xref:System.Object.MemberwiseClone?displayProperty=nameWithType>|<xref:System.Object.GetType?displayProperty=nameWithType>|  
|<span data-ttu-id="85c16-105"><xref:System.Object.ToString?displayProperty=nameWithType> pour les types binaires tels que `BINARY`, `VARBINARY`, `IMAGE` et `TIMESTAMP`.</span><span class="sxs-lookup"><span data-stu-id="85c16-105"><xref:System.Object.ToString?displayProperty=nameWithType> for binary types such as `BINARY`, `VARBINARY`, `IMAGE`, and `TIMESTAMP`.</span></span>||  
  
## <a name="differences-from-net"></a><span data-ttu-id="85c16-106">Différences par rapport à .NET</span><span class="sxs-lookup"><span data-stu-id="85c16-106">Differences from .NET</span></span>  

 <span data-ttu-id="85c16-107">La sortie de <xref:System.Object.ToString?displayProperty=nameWithType> pour double utilise SQL `CONVERT` (nvarchar (30), @x , 2) sur SQL.</span><span class="sxs-lookup"><span data-stu-id="85c16-107">The output of <xref:System.Object.ToString?displayProperty=nameWithType> for double uses SQL `CONVERT`(NVARCHAR(30), @x, 2) on SQL.</span></span> <span data-ttu-id="85c16-108">SQL utilise toujours 16 chiffres et une notation scientifique dans ce cas (par exemple, "0.000000000000000e+000" pour 0).</span><span class="sxs-lookup"><span data-stu-id="85c16-108">SQL always uses 16 digits and scientific notation in this case (for example, "0.000000000000000e+000" for 0).</span></span> <span data-ttu-id="85c16-109">Par conséquent, la conversion <xref:System.Object.ToString?displayProperty=nameWithType> ne génère pas la même chaîne que <xref:System.Convert.ToString%2A?displayProperty=nameWithType> dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="85c16-109">As a result, <xref:System.Object.ToString?displayProperty=nameWithType> conversion does not produce the same string as <xref:System.Convert.ToString%2A?displayProperty=nameWithType> in the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85c16-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85c16-110">See also</span></span>

- [<span data-ttu-id="85c16-111">Fonctions et types de données</span><span class="sxs-lookup"><span data-stu-id="85c16-111">Data Types and Functions</span></span>](data-types-and-functions.md)
