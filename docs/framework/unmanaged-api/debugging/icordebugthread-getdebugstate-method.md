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
ms.openlocfilehash: 746fef3629e6573d7dfe47d5a3fcf9ee9a1d4250
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728041"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="bb7ec-102">ICorDebugThread::GetDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="bb7ec-102">ICorDebugThread::GetDebugState Method</span></span>

<span data-ttu-id="bb7ec-103">Obtient l’état de débogage actuel de cet objet ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="bb7ec-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb7ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb7ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb7ec-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bb7ec-105">Parameters</span></span>  

 `pState`  
 <span data-ttu-id="bb7ec-106">à Pointeur vers une combinaison d’opérations de bits de valeurs d’énumération CorDebugThreadState qui décrit l’état de débogage actuel de ce thread.</span><span class="sxs-lookup"><span data-stu-id="bb7ec-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb7ec-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="bb7ec-107">Remarks</span></span>  

 <span data-ttu-id="bb7ec-108">Si le processus est actuellement arrêté, `pState` représente l’état de débogage qui existe pour ce thread si le processus devait être poursuivi, et non l’état actuel réel de ce thread.</span><span class="sxs-lookup"><span data-stu-id="bb7ec-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb7ec-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bb7ec-109">Requirements</span></span>  

 <span data-ttu-id="bb7ec-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb7ec-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb7ec-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb7ec-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb7ec-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb7ec-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb7ec-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb7ec-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
