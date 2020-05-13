---
title: ICorDebugManagedCallback::EvalComplete, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalComplete
helpviewer_keywords:
- ICorDebugManagedCallback::EvalComplete method [.NET Framework debugging]
- EvalComplete method [.NET Framework debugging]
ms.assetid: f74ab4eb-cd1b-407c-a66d-8ec0d85647f3
topic_type:
- apiref
ms.openlocfilehash: 0431b54997c9889e2b3206392e86e4dcde45ffb3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212449"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="4e03b-102">ICorDebugManagedCallback::EvalComplete, méthode</span><span class="sxs-lookup"><span data-stu-id="4e03b-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="4e03b-103">Notifie le débogueur qu’une évaluation est terminée.</span><span class="sxs-lookup"><span data-stu-id="4e03b-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e03b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e03b-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e03b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4e03b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="4e03b-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel l’évaluation a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="4e03b-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="4e03b-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread dans lequel l’évaluation a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="4e03b-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="4e03b-108">dans Pointeur vers un objet ICorDebugEval qui représente le code qui a effectué l’évaluation.</span><span class="sxs-lookup"><span data-stu-id="4e03b-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e03b-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4e03b-109">Requirements</span></span>  
 <span data-ttu-id="4e03b-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e03b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e03b-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e03b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e03b-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e03b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e03b-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e03b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e03b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e03b-114">See also</span></span>

- [<span data-ttu-id="4e03b-115">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="4e03b-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
