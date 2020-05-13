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
ms.openlocfilehash: 62d45da44a95eae399fbbd287aa997a5f913d0b0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209654"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="f0b6f-102">ICorDebugProcess5::GetGCHeapInformation, méthode</span><span class="sxs-lookup"><span data-stu-id="f0b6f-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="f0b6f-103">Fournit des informations générales sur le tas garbage collection, y compris s’il est actuellement énumérable.</span><span class="sxs-lookup"><span data-stu-id="f0b6f-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0b6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0b6f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0b6f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0b6f-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="f0b6f-106">à Pointeur vers une valeur [COR_HEAPINFO](cor-heapinfo-structure.md) qui fournit des informations générales sur le tas garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f0b6f-106">[out] A pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0b6f-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="f0b6f-107">Remarks</span></span>  
 <span data-ttu-id="f0b6f-108">La `ICorDebugProcess5::GetGCHeapInformation` méthode doit être appelée avant d’énumérer le tas ou les régions de tas individuelles pour garantir que les structures de garbage collection dans le processus sont actuellement valides.</span><span class="sxs-lookup"><span data-stu-id="f0b6f-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="f0b6f-109">Le tas garbage collection ne peut pas être parcouru tant qu’une collection est en cours.</span><span class="sxs-lookup"><span data-stu-id="f0b6f-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="f0b6f-110">Dans le cas contraire, l’énumération peut capturer des structures de garbage collection qui ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="f0b6f-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0b6f-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f0b6f-111">Requirements</span></span>  
 <span data-ttu-id="f0b6f-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0b6f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0b6f-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0b6f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0b6f-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0b6f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0b6f-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0b6f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0b6f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0b6f-116">See also</span></span>

- [<span data-ttu-id="f0b6f-117">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="f0b6f-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="f0b6f-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="f0b6f-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
