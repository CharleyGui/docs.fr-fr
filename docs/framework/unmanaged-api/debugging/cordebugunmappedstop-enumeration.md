---
title: CorDebugUnmappedStop, énumération
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
ms.openlocfilehash: cc02f63808b1929b93777c8bbc67c47000b0b424
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132744"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="0ebea-102">CorDebugUnmappedStop, énumération</span><span class="sxs-lookup"><span data-stu-id="0ebea-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="0ebea-103">Spécifie le type de code non mappé qui peut déclencher un arrêt dans l'exécution du code par l'exécution pas à pas.</span><span class="sxs-lookup"><span data-stu-id="0ebea-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ebea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ebea-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a><span data-ttu-id="0ebea-105">Membres</span><span class="sxs-lookup"><span data-stu-id="0ebea-105">Members</span></span>  
  
|<span data-ttu-id="0ebea-106">Membre</span><span class="sxs-lookup"><span data-stu-id="0ebea-106">Member</span></span>|<span data-ttu-id="0ebea-107">Description</span><span class="sxs-lookup"><span data-stu-id="0ebea-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="0ebea-108">Ne pas arrêter dans un type de code non mappé.</span><span class="sxs-lookup"><span data-stu-id="0ebea-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="0ebea-109">Arrêtez dans le code de prologue.</span><span class="sxs-lookup"><span data-stu-id="0ebea-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="0ebea-110">Arrêtez dans le code d’épilogue.</span><span class="sxs-lookup"><span data-stu-id="0ebea-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="0ebea-111">Arrêter dans le code qui n’a pas d’informations de mappage.</span><span class="sxs-lookup"><span data-stu-id="0ebea-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="0ebea-112">Arrêtez dans du code non mappé qui ne tient pas dans la catégorie prologue, épilogue, no-Mapping-information ou non managé.</span><span class="sxs-lookup"><span data-stu-id="0ebea-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="0ebea-113">Arrêtez dans le code non managé.</span><span class="sxs-lookup"><span data-stu-id="0ebea-113">Stop in unmanaged code.</span></span> <span data-ttu-id="0ebea-114">Cette valeur est valide uniquement avec le débogage d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="0ebea-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="0ebea-115">Arrêtez dans tous les types de code non mappé.</span><span class="sxs-lookup"><span data-stu-id="0ebea-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ebea-116">Notes</span><span class="sxs-lookup"><span data-stu-id="0ebea-116">Remarks</span></span>  
 <span data-ttu-id="0ebea-117">Utilisez la méthode [ICorDebugStepper :: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) pour définir les indicateurs qui spécifient le code non mappé dans lequel le pas à pas s’arrêtera.</span><span class="sxs-lookup"><span data-stu-id="0ebea-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ebea-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="0ebea-118">Requirements</span></span>  
 <span data-ttu-id="0ebea-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ebea-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ebea-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ebea-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ebea-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ebea-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ebea-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ebea-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ebea-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ebea-123">See also</span></span>

- [<span data-ttu-id="0ebea-124">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="0ebea-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
