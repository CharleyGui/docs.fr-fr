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
ms.openlocfilehash: 33a68d11a8d17e46533b4f83bbf87aafe171e612
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212397"
---
# <a name="icordebugmanagedcallbackcontrolctrap-method"></a><span data-ttu-id="3f3dd-102">ICorDebugManagedCallback::ControlCTrap, méthode</span><span class="sxs-lookup"><span data-stu-id="3f3dd-102">ICorDebugManagedCallback::ControlCTrap Method</span></span>
<span data-ttu-id="3f3dd-103">Notifie le débogueur qu’un CTRL + C est intercepté dans le processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="3f3dd-103">Notifies the debugger that a CTRL+C is trapped in the process that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f3dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f3dd-104">Syntax</span></span>  
  
```cpp  
HRESULT ControlCTrap (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f3dd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3f3dd-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="3f3dd-106">dans Pointeur vers un objet ICorDebugProcess qui représente le processus dans lequel CTRL + C est intercepté.</span><span class="sxs-lookup"><span data-stu-id="3f3dd-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the CTRL+C is trapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f3dd-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3f3dd-107">Return Value</span></span>  
  
|<span data-ttu-id="3f3dd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f3dd-108">HRESULT</span></span>|<span data-ttu-id="3f3dd-109">Description</span><span class="sxs-lookup"><span data-stu-id="3f3dd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f3dd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3f3dd-110">S_OK</span></span>|<span data-ttu-id="3f3dd-111">Le débogueur gère l’interruption CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="3f3dd-111">The debugger will handle the CTRL+C trap.</span></span>|  
|<span data-ttu-id="3f3dd-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="3f3dd-112">S_FALSE</span></span>|<span data-ttu-id="3f3dd-113">Le débogueur ne gère pas l’interruption CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="3f3dd-113">The debugger will not handle the CTRL+C trap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f3dd-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="3f3dd-114">Remarks</span></span>  
 <span data-ttu-id="3f3dd-115">Tous les domaines d’application au sein du processus sont arrêtés pour ce rappel.</span><span class="sxs-lookup"><span data-stu-id="3f3dd-115">All application domains within the process are stopped for this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f3dd-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3f3dd-116">Requirements</span></span>  
 <span data-ttu-id="3f3dd-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f3dd-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f3dd-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f3dd-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f3dd-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f3dd-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f3dd-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f3dd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f3dd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f3dd-121">See also</span></span>

- [<span data-ttu-id="3f3dd-122">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="3f3dd-122">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
