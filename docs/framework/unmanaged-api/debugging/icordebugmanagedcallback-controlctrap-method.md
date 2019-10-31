---
title: ICorDebugManagedCallback::ControlCTrap, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ControlCTrap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ControlCTrap
helpviewer_keywords:
- ICorDebugManagedCallback::ControlCTrap method [.NET Framework debugging]
- ControlCTrap method [.NET Framework debugging]
ms.assetid: 0500854e-2121-43d9-a028-64312da35258
topic_type:
- apiref
ms.openlocfilehash: da35db8a943fda5fb3fbf4126684bb9cb7243001
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137426"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="1f5aa-102">ICorDebugManagedCallback::ControlCTrap, méthode</span><span class="sxs-lookup"><span data-stu-id="1f5aa-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="1f5aa-103">Notifie le débogueur qu’un CTRL + C est intercepté dans le processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="1f5aa-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f5aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f5aa-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f5aa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1f5aa-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="1f5aa-106">dans Pointeur vers un objet ICorDebugProcess qui représente le processus dans lequel CTRL + C est intercepté.</span><span class="sxs-lookup"><span data-stu-id="1f5aa-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f5aa-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1f5aa-107">Return Value</span></span>  
  
|<span data-ttu-id="1f5aa-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f5aa-108">HRESULT</span></span>|<span data-ttu-id="1f5aa-109">Description</span><span class="sxs-lookup"><span data-stu-id="1f5aa-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f5aa-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f5aa-110">S_OK</span></span>|<span data-ttu-id="1f5aa-111">Le débogueur gère l’interruption CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="1f5aa-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="1f5aa-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1f5aa-112">S_FALSE</span></span>|<span data-ttu-id="1f5aa-113">Le débogueur ne gère pas l’interruption CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="1f5aa-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f5aa-114">Notes</span><span class="sxs-lookup"><span data-stu-id="1f5aa-114">Remarks</span></span>  
 <span data-ttu-id="1f5aa-115">Tous les domaines d’application au sein du processus sont arrêtés pour ce rappel.</span><span class="sxs-lookup"><span data-stu-id="1f5aa-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f5aa-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="1f5aa-116">Requirements</span></span>  
 <span data-ttu-id="1f5aa-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f5aa-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f5aa-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f5aa-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f5aa-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f5aa-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f5aa-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f5aa-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f5aa-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f5aa-121">See also</span></span>

- [<span data-ttu-id="1f5aa-122">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="1f5aa-122">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
