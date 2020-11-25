---
title: COR_PRF_RUNTIME_TYPE, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_RUNTIME_TYPE Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_RUNTIME_TYPE
helpviewer_keywords:
- COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type:
- apiref
ms.openlocfilehash: b599a97f414491ff80000f99551a727b86ae13de
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696750"
---
# <a name="cor_prf_runtime_type-enumeration"></a><span data-ttu-id="e1b0e-102">COR_PRF_RUNTIME_TYPE, énumération</span><span class="sxs-lookup"><span data-stu-id="e1b0e-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>

<span data-ttu-id="e1b0e-103">Contient des valeurs qui indiquent la version du common language runtime (CLR) : Desktop ou CoreCLR, qui est utilisé dans Silverlight.</span><span class="sxs-lookup"><span data-stu-id="e1b0e-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1b0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1b0e-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="e1b0e-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e1b0e-105">Members</span></span>  
  
|<span data-ttu-id="e1b0e-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e1b0e-106">Member</span></span>|<span data-ttu-id="e1b0e-107">Description</span><span class="sxs-lookup"><span data-stu-id="e1b0e-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="e1b0e-108">Version de bureau du CLR.</span><span class="sxs-lookup"><span data-stu-id="e1b0e-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="e1b0e-109">Version principale du CLR, utilisée dans Silverlight.</span><span class="sxs-lookup"><span data-stu-id="e1b0e-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1b0e-110">Notes</span><span class="sxs-lookup"><span data-stu-id="e1b0e-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1b0e-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e1b0e-111">Requirements</span></span>  

 <span data-ttu-id="e1b0e-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1b0e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1b0e-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1b0e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1b0e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1b0e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1b0e-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1b0e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1b0e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1b0e-116">See also</span></span>

- [<span data-ttu-id="e1b0e-117">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="e1b0e-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
