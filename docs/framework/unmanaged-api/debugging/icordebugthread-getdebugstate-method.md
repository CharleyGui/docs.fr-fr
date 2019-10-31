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
ms.openlocfilehash: f054f8f2bd7c322e722a1e17290ba6fbad9e37b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133511"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="34bfb-102">ICorDebugThread::GetDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="34bfb-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="34bfb-103">Obtient l’état de débogage actuel de cet objet ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="34bfb-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34bfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34bfb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34bfb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="34bfb-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="34bfb-106">à Pointeur vers une combinaison d’opérations de bits de valeurs d’énumération CorDebugThreadState qui décrit l’état de débogage actuel de ce thread.</span><span class="sxs-lookup"><span data-stu-id="34bfb-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34bfb-107">Notes</span><span class="sxs-lookup"><span data-stu-id="34bfb-107">Remarks</span></span>  
 <span data-ttu-id="34bfb-108">Si le processus est actuellement arrêté, `pState` représente l’état de débogage qui existe pour ce thread si le processus devait être poursuivi, et non l’état actuel réel de ce thread.</span><span class="sxs-lookup"><span data-stu-id="34bfb-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34bfb-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="34bfb-109">Requirements</span></span>  
 <span data-ttu-id="34bfb-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34bfb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34bfb-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34bfb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34bfb-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34bfb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34bfb-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34bfb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
