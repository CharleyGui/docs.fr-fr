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
ms.openlocfilehash: 0e9ed8054711297173e880c9eecb12c3f5bd0a68
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207138"
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="34934-102">ICorDebugManagedCallback::CreateProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="34934-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="34934-103">Notifie le débogueur lorsqu’un processus a été attaché ou démarré pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="34934-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34934-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34934-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34934-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="34934-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="34934-106">dans Pointeur vers un objet ICorDebugProcess qui représente le processus qui a été attaché ou démarré.</span><span class="sxs-lookup"><span data-stu-id="34934-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34934-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="34934-107">Remarks</span></span>  
 <span data-ttu-id="34934-108">Cette méthode n’est pas appelée tant que le common language runtime n’est pas initialisé.</span><span class="sxs-lookup"><span data-stu-id="34934-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="34934-109">La plupart des méthodes [ICorDebug](icordebug-interface.md) retournent CORDBG_E_NOTREADY avant le `CreateProcess` rappel.</span><span class="sxs-lookup"><span data-stu-id="34934-109">Most of the [ICorDebug](icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34934-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="34934-110">Requirements</span></span>  
 <span data-ttu-id="34934-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34934-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34934-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34934-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34934-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34934-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34934-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34934-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34934-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34934-115">See also</span></span>

- [<span data-ttu-id="34934-116">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="34934-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
