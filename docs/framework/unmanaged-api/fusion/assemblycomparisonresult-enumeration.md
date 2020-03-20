---
title: AssemblyComparisonResult, énumération
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
ms.openlocfilehash: e3cdb648397ca4f4aa2326e4f2349a5a14c3edcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178288"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="d09df-102">AssemblyComparisonResult, énumération</span><span class="sxs-lookup"><span data-stu-id="d09df-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="d09df-103">Indique l’équivalence de deux identités d’assemblage, déterminée par la fonction [CompareAssemblyIdentity.](compareassemblyidentity-function.md)</span><span class="sxs-lookup"><span data-stu-id="d09df-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d09df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d09df-104">Syntax</span></span>  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a><span data-ttu-id="d09df-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d09df-105">Members</span></span>  
  
|<span data-ttu-id="d09df-106">Nom de membre</span><span class="sxs-lookup"><span data-stu-id="d09df-106">Member name</span></span>|<span data-ttu-id="d09df-107">Description</span><span class="sxs-lookup"><span data-stu-id="d09df-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="d09df-108">Indique que tous les champs d’assemblage dans la correspondance de comparaison.</span><span class="sxs-lookup"><span data-stu-id="d09df-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="d09df-109">Indique que les assemblages sont considérés comme équivalents en fonction de l’unification de la version en cours d’exécution (CLR) des numéros de version d’assemblage dans la version cadre .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="d09df-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="d09df-110">Indique une correspondance partielle des assemblées basée sur l’unification CLR des numéros de version d’assemblage dans le cadre .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="d09df-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="d09df-111">Indique une correspondance partielle des assemblées.</span><span class="sxs-lookup"><span data-stu-id="d09df-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="d09df-112">Indique une correspondance partielle des assemblages basée sur l’unification héritée des nombres de versions.</span><span class="sxs-lookup"><span data-stu-id="d09df-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="d09df-113">Indique une correspondance partielle d’assemblages simplement nommés.</span><span class="sxs-lookup"><span data-stu-id="d09df-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="d09df-114">Indique que les assemblages sont considérés comme équivalents en fonction de l’unification CLR des numéros de version dans les versions héritées du cadre .NET.</span><span class="sxs-lookup"><span data-stu-id="d09df-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="d09df-115">Indique une correspondance entre deux assemblées simplement nommées dont les numéros de version ont été ignorés.</span><span class="sxs-lookup"><span data-stu-id="d09df-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="d09df-116">Indique qu’aucun match n’a eu lieu entre les deux assemblées.</span><span class="sxs-lookup"><span data-stu-id="d09df-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="d09df-117">Indique que les deux assemblages correspondent à l’exception de leurs numéros de version, qui ne correspondent que partiellement.</span><span class="sxs-lookup"><span data-stu-id="d09df-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="d09df-118">Indique que les deux assemblages correspondent à l’exception de leurs numéros de version, qui ne correspondent pas.</span><span class="sxs-lookup"><span data-stu-id="d09df-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="d09df-119">Indique que la raison de la non-équivalence n’est pas connue.</span><span class="sxs-lookup"><span data-stu-id="d09df-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d09df-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d09df-120">Requirements</span></span>  
 <span data-ttu-id="d09df-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d09df-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d09df-122">**En-tête:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d09df-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d09df-123">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d09df-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d09df-124">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d09df-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09df-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d09df-125">See also</span></span>

- [<span data-ttu-id="d09df-126">CompareAssemblyIdentity, fonction</span><span class="sxs-lookup"><span data-stu-id="d09df-126">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="d09df-127">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="d09df-127">Fusion Enumerations</span></span>](fusion-enumerations.md)
