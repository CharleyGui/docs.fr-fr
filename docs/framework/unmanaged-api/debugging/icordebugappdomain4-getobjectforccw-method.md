---
title: ICorDebugAppDomain4::GetObjectForCCW, méthode
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: f3e64def16fb2817244ef7669ff4bb7fef0bd07c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684446"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="6fd76-102">ICorDebugAppDomain4::GetObjectForCCW, méthode</span><span class="sxs-lookup"><span data-stu-id="6fd76-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>

<span data-ttu-id="6fd76-103">Obtient un objet managé à partir d'un pointeur de wrapper CCW (COM Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="6fd76-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fd76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fd76-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fd76-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6fd76-105">Parameters</span></span>  

 `ccwPointer`  
 <span data-ttu-id="6fd76-106">[in] Pointeur vers un wrapper CCW (COM Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="6fd76-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="6fd76-107">à Pointeur vers l’adresse d’un objet « ICorDebugValue » qui représente l’objet managé qui correspond au pointeur CCW donné.</span><span class="sxs-lookup"><span data-stu-id="6fd76-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fd76-108">Notes</span><span class="sxs-lookup"><span data-stu-id="6fd76-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fd76-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6fd76-109">Requirements</span></span>  

 <span data-ttu-id="6fd76-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fd76-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fd76-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fd76-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fd76-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fd76-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fd76-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fd76-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fd76-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fd76-114">See also</span></span>

- [<span data-ttu-id="6fd76-115">ICorDebugAppDomain4 (interface)</span><span class="sxs-lookup"><span data-stu-id="6fd76-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="6fd76-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6fd76-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
