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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6c417eec9583ff069c9d61fa31e9c14f3931130
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778511"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="ccffc-102">AssemblyComparisonResult, énumération</span><span class="sxs-lookup"><span data-stu-id="ccffc-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="ccffc-103">Indique l’équivalence de deux identités d’assembly, tel que déterminé par le [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="ccffc-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccffc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccffc-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ccffc-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ccffc-105">Members</span></span>  
  
|<span data-ttu-id="ccffc-106">Nom de membre</span><span class="sxs-lookup"><span data-stu-id="ccffc-106">Member name</span></span>|<span data-ttu-id="ccffc-107">Description</span><span class="sxs-lookup"><span data-stu-id="ccffc-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="ccffc-108">Indique qu’assembly tous les champs dans la correspondance de comparaison.</span><span class="sxs-lookup"><span data-stu-id="ccffc-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="ccffc-109">Indique que les assemblys sont considérées comme équivalentes en fonction de l’unification de version (CLR) common language runtime des numéros de version d’assembly dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="ccffc-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="ccffc-110">Indique une correspondance partielle des assemblys selon l’unification CLR des numéros de version d’assembly dans le .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="ccffc-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="ccffc-111">Indique une correspondance partielle des assemblys.</span><span class="sxs-lookup"><span data-stu-id="ccffc-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="ccffc-112">Indique une correspondance partielle des assemblys selon l’unification héritée des numéros de version.</span><span class="sxs-lookup"><span data-stu-id="ccffc-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="ccffc-113">Indique une correspondance partielle des assemblys nommés simplement.</span><span class="sxs-lookup"><span data-stu-id="ccffc-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="ccffc-114">Indique que les assemblys sont considérées comme équivalentes en fonction de l’unification des numéros de version dans les versions héritées du .NET Framework CLR.</span><span class="sxs-lookup"><span data-stu-id="ccffc-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="ccffc-115">Indique une correspondance entre deux assemblys simplement nommés dont les numéros de version ont été ignorés.</span><span class="sxs-lookup"><span data-stu-id="ccffc-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="ccffc-116">Indique qu’aucune correspondance s’est produite entre les deux assemblys.</span><span class="sxs-lookup"><span data-stu-id="ccffc-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="ccffc-117">Indique que les deux assemblys correspondent à l’exception de leurs numéros de version correspondent uniquement partiellement.</span><span class="sxs-lookup"><span data-stu-id="ccffc-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="ccffc-118">Indique que les deux assemblys correspondent à l’exception de leurs numéros de version qui ne correspondent pas.</span><span class="sxs-lookup"><span data-stu-id="ccffc-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="ccffc-119">Indique que la raison de non-équivalence n’est pas connue.</span><span class="sxs-lookup"><span data-stu-id="ccffc-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ccffc-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ccffc-120">Requirements</span></span>  
 <span data-ttu-id="ccffc-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccffc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccffc-122">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ccffc-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ccffc-123">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ccffc-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ccffc-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccffc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccffc-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccffc-125">See also</span></span>

- [<span data-ttu-id="ccffc-126">CompareAssemblyIdentity, fonction</span><span class="sxs-lookup"><span data-stu-id="ccffc-126">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)
- [<span data-ttu-id="ccffc-127">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="ccffc-127">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
