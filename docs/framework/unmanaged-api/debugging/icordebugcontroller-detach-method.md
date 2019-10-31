---
title: ICorDebugController::Detach, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
ms.openlocfilehash: b98077914d680c908587649fdd517aca9c8dcd40
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125429"
---
# <a name="icordebugcontrollerdetach-method"></a><span data-ttu-id="5a98e-102">ICorDebugController::Detach, méthode</span><span class="sxs-lookup"><span data-stu-id="5a98e-102">ICorDebugController::Detach Method</span></span>
<span data-ttu-id="5a98e-103">Détache le débogueur du processus ou du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="5a98e-103">Detaches the debugger from the process or application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a98e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a98e-104">Syntax</span></span>  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5a98e-105">Notes</span><span class="sxs-lookup"><span data-stu-id="5a98e-105">Remarks</span></span>  
 <span data-ttu-id="5a98e-106">Le processus ou le domaine d’application continue l’exécution normalement, mais l’objet « ICorDebugProcess » ou « ICorDebugAppDomain » n’est plus valide et aucun autre rappel ne se produit.</span><span class="sxs-lookup"><span data-stu-id="5a98e-106">The process or application domain continues execution normally, but the "ICorDebugProcess" or "ICorDebugAppDomain" object is no longer valid and no further callbacks will occur.</span></span>  
  
 <span data-ttu-id="5a98e-107">Dans la version de .NET Framework 2,0, si le débogage non managé est activé, cette méthode échouera en raison des limitations du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="5a98e-107">In the .NET Framework version 2.0, if unmanaged debugging is enabled, this method will fail due to operating system limitations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a98e-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="5a98e-108">Requirements</span></span>  
 <span data-ttu-id="5a98e-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a98e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a98e-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a98e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a98e-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a98e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a98e-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a98e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a98e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a98e-113">See also</span></span>
