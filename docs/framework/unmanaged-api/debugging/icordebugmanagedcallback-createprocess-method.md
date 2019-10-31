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
ms.openlocfilehash: d773368c85fd42fd169109cf1c7e6635705ebb7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090228"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="4e818-102">ICorDebugManagedCallback::CreateProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="4e818-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="4e818-103">Notifie le débogueur lorsqu’un processus a été attaché ou démarré pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="4e818-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e818-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e818-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e818-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4e818-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="4e818-106">dans Pointeur vers un objet ICorDebugProcess qui représente le processus qui a été attaché ou démarré.</span><span class="sxs-lookup"><span data-stu-id="4e818-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e818-107">Notes</span><span class="sxs-lookup"><span data-stu-id="4e818-107">Remarks</span></span>  
 <span data-ttu-id="4e818-108">Cette méthode n’est pas appelée tant que le common language runtime n’est pas initialisé.</span><span class="sxs-lookup"><span data-stu-id="4e818-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="4e818-109">La plupart des méthodes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) retournent CORDBG_E_NOTREADY avant le rappel `CreateProcess`.</span><span class="sxs-lookup"><span data-stu-id="4e818-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e818-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="4e818-110">Requirements</span></span>  
 <span data-ttu-id="4e818-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e818-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e818-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e818-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e818-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e818-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e818-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e818-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e818-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e818-115">See also</span></span>

- [<span data-ttu-id="4e818-116">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="4e818-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
