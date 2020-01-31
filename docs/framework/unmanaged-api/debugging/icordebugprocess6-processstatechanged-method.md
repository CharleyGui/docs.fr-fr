---
title: ICorDebugProcess6::ProcessStateChanged, méthode
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: b6665df550a2d07a3fa84c3f2b6bf07f459cd713
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792201"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="50cdd-102">ICorDebugProcess6::ProcessStateChanged, méthode</span><span class="sxs-lookup"><span data-stu-id="50cdd-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="50cdd-103">Informe [ICorDebug](icordebug-interface.md) que le processus est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="50cdd-103">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50cdd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50cdd-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50cdd-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="50cdd-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="50cdd-106">dans Membre de l’énumération [processstatechanged,](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="50cdd-106">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50cdd-107">Notes</span><span class="sxs-lookup"><span data-stu-id="50cdd-107">Remarks</span></span>  
 <span data-ttu-id="50cdd-108">Le débogueur appelle cette méthode pour notifier [ICorDebug](icordebug-interface.md) que le processus est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="50cdd-108">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50cdd-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="50cdd-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50cdd-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="50cdd-110">Requirements</span></span>  
 <span data-ttu-id="50cdd-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50cdd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50cdd-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50cdd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50cdd-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50cdd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50cdd-114">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50cdd-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50cdd-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50cdd-115">See also</span></span>

- [<span data-ttu-id="50cdd-116">ICorDebugProcess6, interface</span><span class="sxs-lookup"><span data-stu-id="50cdd-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="50cdd-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="50cdd-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
