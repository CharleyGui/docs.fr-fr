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
ms.openlocfilehash: 13125f60f596cb8a80d9c42c51a979f632de494b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379756"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="df362-102">ICorDebugThread::GetDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="df362-102">ICorDebugThread::GetDebugState Method</span></span>
<span data-ttu-id="df362-103">Obtient l’état de débogage actuel de cet objet ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="df362-103">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df362-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df362-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df362-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df362-105">Parameters</span></span>  
 `pState`  
 <span data-ttu-id="df362-106">à Pointeur vers une combinaison d’opérations de bits de valeurs d’énumération CorDebugThreadState qui décrit l’état de débogage actuel de ce thread.</span><span class="sxs-lookup"><span data-stu-id="df362-106">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df362-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="df362-107">Remarks</span></span>  
 <span data-ttu-id="df362-108">Si le processus est actuellement arrêté, `pState` représente l’état de débogage qui existe pour ce thread si le processus devait être poursuivi, et non l’état actuel réel de ce thread.</span><span class="sxs-lookup"><span data-stu-id="df362-108">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df362-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="df362-109">Requirements</span></span>  
 <span data-ttu-id="df362-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df362-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df362-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df362-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df362-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df362-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df362-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df362-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
