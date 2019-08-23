---
title: ICorDebugProcess6::ProcessStateChanged, méthode
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb158b383745cd7e44c8fede6ddd43ae81ced2d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930762"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="cc2dd-102">ICorDebugProcess6::ProcessStateChanged, méthode</span><span class="sxs-lookup"><span data-stu-id="cc2dd-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="cc2dd-103">Informe [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) que le processus est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="cc2dd-103">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc2dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc2dd-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc2dd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cc2dd-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="cc2dd-106">dans Membre de l’énumération [processstatechanged,](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="cc2dd-106">[in] A member of the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc2dd-107">Notes</span><span class="sxs-lookup"><span data-stu-id="cc2dd-107">Remarks</span></span>  
 <span data-ttu-id="cc2dd-108">Le débogueur appelle cette méthode pour notifier [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) que le processus est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="cc2dd-108">The debugger calls this method to notify [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc2dd-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cc2dd-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc2dd-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cc2dd-110">Requirements</span></span>  
 <span data-ttu-id="cc2dd-111">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc2dd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc2dd-112">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc2dd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc2dd-113">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc2dd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc2dd-114">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc2dd-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc2dd-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc2dd-115">See also</span></span>

- [<span data-ttu-id="cc2dd-116">ICorDebugProcess6, interface</span><span class="sxs-lookup"><span data-stu-id="cc2dd-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="cc2dd-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="cc2dd-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
