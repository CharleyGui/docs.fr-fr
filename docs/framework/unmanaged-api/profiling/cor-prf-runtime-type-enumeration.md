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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c52f96ad9458dfd5cdedc5cc73154aa570c6759
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751965"
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="d7a95-102">COR_PRF_RUNTIME_TYPE, énumération</span><span class="sxs-lookup"><span data-stu-id="d7a95-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="d7a95-103">Contient des valeurs qui indiquent la version du common language runtime (CLR) : bureau ou CoreCLR, qui est utilisé dans Silverlight.</span><span class="sxs-lookup"><span data-stu-id="d7a95-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7a95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7a95-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="d7a95-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d7a95-105">Members</span></span>  
  
|<span data-ttu-id="d7a95-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d7a95-106">Member</span></span>|<span data-ttu-id="d7a95-107">Description</span><span class="sxs-lookup"><span data-stu-id="d7a95-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="d7a95-108">La version du CLR de bureau.</span><span class="sxs-lookup"><span data-stu-id="d7a95-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="d7a95-109">La version principale du CLR, utilisée dans Silverlight.</span><span class="sxs-lookup"><span data-stu-id="d7a95-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7a95-110">Notes</span><span class="sxs-lookup"><span data-stu-id="d7a95-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7a95-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d7a95-111">Requirements</span></span>  
 <span data-ttu-id="d7a95-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7a95-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7a95-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d7a95-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d7a95-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7a95-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7a95-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7a95-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7a95-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7a95-116">See also</span></span>

- [<span data-ttu-id="d7a95-117">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="d7a95-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
