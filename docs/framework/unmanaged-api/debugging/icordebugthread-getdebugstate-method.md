---
title: ICorDebugThread::GetDebugState, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0baabbb736365b138d1754e68070207b4310bf57
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762459"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="614f8-102">ICorDebugThread::GetDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="614f8-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="614f8-103">Obtient l’état de débogage actuel de cet objet ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="614f8-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="614f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="614f8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="614f8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="614f8-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="614f8-106">[out] Pointeur vers une combinaison au niveau du bit des valeurs d’énumération CorDebugThreadState qui décrit l’état de débogage actuel de ce thread.</span><span class="sxs-lookup"><span data-stu-id="614f8-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="614f8-107">Notes</span><span class="sxs-lookup"><span data-stu-id="614f8-107">Remarks</span></span>  
 <span data-ttu-id="614f8-108">Si le processus est actuellement arrêté, `pState` représente l’état de débogage qui existerait pour ce thread si le processus de se poursuivre, pas l’état en cours réel de ce thread.</span><span class="sxs-lookup"><span data-stu-id="614f8-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="614f8-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="614f8-109">Requirements</span></span>  
 <span data-ttu-id="614f8-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="614f8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="614f8-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="614f8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="614f8-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="614f8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="614f8-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="614f8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
