---
title: ICorDebugManagedCallback::CreateProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type:
- apiref
ms.openlocfilehash: 0c3059697014cea33081f6cb81b9d93c7d028c2e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777469"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="92f16-102">ICorDebugManagedCallback::CreateProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="92f16-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="92f16-103">Notifie le débogueur lorsqu’un processus a été attaché ou démarré pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="92f16-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f16-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92f16-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92f16-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="92f16-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="92f16-106">dans Pointeur vers un objet ICorDebugProcess qui représente le processus qui a été attaché ou démarré.</span><span class="sxs-lookup"><span data-stu-id="92f16-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92f16-107">Notes</span><span class="sxs-lookup"><span data-stu-id="92f16-107">Remarks</span></span>  
 <span data-ttu-id="92f16-108">Cette méthode n’est pas appelée tant que le common language runtime n’est pas initialisé.</span><span class="sxs-lookup"><span data-stu-id="92f16-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="92f16-109">La plupart des méthodes [ICorDebug](icordebug-interface.md) retournent CORDBG_E_NOTREADY avant le rappel `CreateProcess`.</span><span class="sxs-lookup"><span data-stu-id="92f16-109">Most of the [ICorDebug](icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92f16-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="92f16-110">Requirements</span></span>  
 <span data-ttu-id="92f16-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92f16-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92f16-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92f16-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92f16-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92f16-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92f16-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92f16-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f16-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92f16-115">See also</span></span>

- [<span data-ttu-id="92f16-116">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="92f16-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
