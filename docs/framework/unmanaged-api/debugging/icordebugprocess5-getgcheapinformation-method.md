---
title: ICorDebugProcess5::GetGCHeapInformation, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e94034fcdcd8d86f34c61af30a7729a80c913fac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767347"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="2ec83-102">ICorDebugProcess5::GetGCHeapInformation, méthode</span><span class="sxs-lookup"><span data-stu-id="2ec83-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="2ec83-103">Fournit des informations générales sur le tas de garbage collection, notamment s’il est actuellement énumérable.</span><span class="sxs-lookup"><span data-stu-id="2ec83-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ec83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ec83-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ec83-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="2ec83-106">[out] Un pointeur vers un [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) valeur qui fournit des informations générales sur le tas de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="2ec83-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ec83-107">Notes</span><span class="sxs-lookup"><span data-stu-id="2ec83-107">Remarks</span></span>  
 <span data-ttu-id="2ec83-108">Le `ICorDebugProcess5::GetGCHeapInformation` méthode doit être appelée avant l’énumération du tas ou régions individuelles de tas pour vous assurer que le garbage collection de structures dans le processus n’est valides actuellement.</span><span class="sxs-lookup"><span data-stu-id="2ec83-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="2ec83-109">Le tas de garbage collection ne peut pas être parcouru lorsqu’une collection est en cours.</span><span class="sxs-lookup"><span data-stu-id="2ec83-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="2ec83-110">Sinon, l’énumération peut capturer des structures de garbage collection qui ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="2ec83-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ec83-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2ec83-111">Requirements</span></span>  
 <span data-ttu-id="2ec83-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ec83-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ec83-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ec83-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ec83-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ec83-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ec83-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ec83-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec83-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ec83-116">See also</span></span>

- [<span data-ttu-id="2ec83-117">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="2ec83-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="2ec83-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2ec83-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
