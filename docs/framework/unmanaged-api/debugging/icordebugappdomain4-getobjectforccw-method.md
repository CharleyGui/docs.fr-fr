---
title: ICorDebugAppDomain4::GetObjectForCCW, méthode
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 8b046eb5926bb9aa4738e8fff8e61b0b7c23a3aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088827"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="038b0-102">ICorDebugAppDomain4::GetObjectForCCW, méthode</span><span class="sxs-lookup"><span data-stu-id="038b0-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="038b0-103">Obtient un objet managé à partir d'un pointeur de wrapper CCW (COM Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="038b0-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="038b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="038b0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="038b0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="038b0-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="038b0-106">[in] Pointeur vers un wrapper CCW (COM Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="038b0-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="038b0-107">à Pointeur vers l’adresse d’un objet « ICorDebugValue » qui représente l’objet managé qui correspond au pointeur CCW donné.</span><span class="sxs-lookup"><span data-stu-id="038b0-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="038b0-108">Notes</span><span class="sxs-lookup"><span data-stu-id="038b0-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="038b0-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="038b0-109">Requirements</span></span>  
 <span data-ttu-id="038b0-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="038b0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="038b0-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="038b0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="038b0-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="038b0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="038b0-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="038b0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="038b0-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="038b0-114">See also</span></span>

- [<span data-ttu-id="038b0-115">ICorDebugAppDomain4, interface</span><span class="sxs-lookup"><span data-stu-id="038b0-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [<span data-ttu-id="038b0-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="038b0-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
