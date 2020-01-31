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
ms.openlocfilehash: 703f159c5bc6b73dcd0e770bdeb61f676aae034c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792379"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="6de00-102">ICorDebugProcess5::GetGCHeapInformation, méthode</span><span class="sxs-lookup"><span data-stu-id="6de00-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="6de00-103">Fournit des informations générales sur le tas garbage collection, y compris s’il est actuellement énumérable.</span><span class="sxs-lookup"><span data-stu-id="6de00-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6de00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6de00-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6de00-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="6de00-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="6de00-106">à Pointeur vers une valeur [COR_HEAPINFO](cor-heapinfo-structure.md) qui fournit des informations générales sur le tas garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6de00-106">[out] A pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6de00-107">Notes</span><span class="sxs-lookup"><span data-stu-id="6de00-107">Remarks</span></span>  
 <span data-ttu-id="6de00-108">La méthode `ICorDebugProcess5::GetGCHeapInformation` doit être appelée avant l’énumération du tas ou des régions de tas individuelles pour garantir que les structures garbage collectiones dans le processus sont actuellement valides.</span><span class="sxs-lookup"><span data-stu-id="6de00-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="6de00-109">Le tas garbage collection ne peut pas être parcouru tant qu’une collection est en cours.</span><span class="sxs-lookup"><span data-stu-id="6de00-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="6de00-110">Dans le cas contraire, l’énumération peut capturer des structures de garbage collection qui ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="6de00-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6de00-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="6de00-111">Requirements</span></span>  
 <span data-ttu-id="6de00-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6de00-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6de00-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6de00-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6de00-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6de00-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6de00-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6de00-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de00-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6de00-116">See also</span></span>

- [<span data-ttu-id="6de00-117">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="6de00-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="6de00-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6de00-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
