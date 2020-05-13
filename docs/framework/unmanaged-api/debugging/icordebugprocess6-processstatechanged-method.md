---
title: ICorDebugProcess6::ProcessStateChanged, méthode
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 6be216741e902b15efc3a3ece95cb4a4229960e3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212843"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="8a976-102">ICorDebugProcess6::ProcessStateChanged, méthode</span><span class="sxs-lookup"><span data-stu-id="8a976-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="8a976-103">Informe [ICorDebug](icordebug-interface.md) que le processus est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8a976-103">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a976-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a976-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a976-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a976-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="8a976-106">dans Membre de l’énumération [processstatechanged,](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="8a976-106">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a976-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="8a976-107">Remarks</span></span>  
 <span data-ttu-id="8a976-108">Le débogueur appelle cette méthode pour notifier [ICorDebug](icordebug-interface.md) que le processus est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8a976-108">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a976-109">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8a976-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a976-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8a976-110">Requirements</span></span>  
 <span data-ttu-id="8a976-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a976-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a976-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a976-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a976-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a976-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a976-114">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a976-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a976-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a976-115">See also</span></span>

- [<span data-ttu-id="8a976-116">ICorDebugProcess6, interface</span><span class="sxs-lookup"><span data-stu-id="8a976-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="8a976-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8a976-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
