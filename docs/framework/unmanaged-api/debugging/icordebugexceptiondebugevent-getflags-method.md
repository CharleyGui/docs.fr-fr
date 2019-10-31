---
title: 'Icordebugexceptiondebugevent, :: GetFlags, méthode'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 6c330ce5b375daacdf257eda16fd5e34012f5d69
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084750"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="4b35d-102">Icordebugexceptiondebugevent, :: GetFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="4b35d-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="4b35d-103">Obtient un indicateur qui précise si l'exception peut être interceptée.</span><span class="sxs-lookup"><span data-stu-id="4b35d-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b35d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b35d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b35d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4b35d-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="4b35d-106">à Pointeur vers une valeur [CorDebugExceptionFlags,](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) qui indique si l’exception peut être interceptée.</span><span class="sxs-lookup"><span data-stu-id="4b35d-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b35d-107">Notes</span><span class="sxs-lookup"><span data-stu-id="4b35d-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b35d-108">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4b35d-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b35d-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="4b35d-109">Requirements</span></span>  
 <span data-ttu-id="4b35d-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b35d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b35d-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b35d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b35d-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b35d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b35d-113">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b35d-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b35d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b35d-114">See also</span></span>

- [<span data-ttu-id="4b35d-115">ICorDebugExceptionDebugEvent, interface</span><span class="sxs-lookup"><span data-stu-id="4b35d-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="4b35d-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4b35d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
