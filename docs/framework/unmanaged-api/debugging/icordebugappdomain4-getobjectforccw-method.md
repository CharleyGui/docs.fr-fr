---
title: Méthode ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 50f46394c809321f0bd256e4c8d75b76fc7c2c70
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784861"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="4762c-102">Méthode ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="4762c-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="4762c-103">Obtient un objet managé à partir d'un pointeur de wrapper CCW (COM Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="4762c-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4762c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4762c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4762c-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="4762c-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="4762c-106">[in] Pointeur vers un wrapper CCW (COM Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="4762c-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="4762c-107">à Pointeur vers l’adresse d’un objet « ICorDebugValue » qui représente l’objet managé qui correspond au pointeur CCW donné.</span><span class="sxs-lookup"><span data-stu-id="4762c-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4762c-108">Notes</span><span class="sxs-lookup"><span data-stu-id="4762c-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4762c-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="4762c-109">Requirements</span></span>  
 <span data-ttu-id="4762c-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4762c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4762c-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4762c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4762c-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4762c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4762c-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4762c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4762c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4762c-114">See also</span></span>

- [<span data-ttu-id="4762c-115">ICorDebugAppDomain4, interface</span><span class="sxs-lookup"><span data-stu-id="4762c-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="4762c-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4762c-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
