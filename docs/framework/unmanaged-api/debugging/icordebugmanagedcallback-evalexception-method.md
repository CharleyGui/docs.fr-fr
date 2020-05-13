---
title: ICorDebugManagedCallback::EvalException, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type:
- apiref
ms.openlocfilehash: 20a841006d51671a491e11c4e40287baf739d191
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209823"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="ac75a-102">ICorDebugManagedCallback::EvalException, méthode</span><span class="sxs-lookup"><span data-stu-id="ac75a-102">ICorDebugManagedCallback::EvalException Method</span></span>
<span data-ttu-id="ac75a-103">Notifie le débogueur qu’une évaluation s’est terminée par une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="ac75a-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac75a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac75a-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac75a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ac75a-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ac75a-106">dans Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel l’évaluation s’est terminée.</span><span class="sxs-lookup"><span data-stu-id="ac75a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ac75a-107">dans Pointeur vers un objet ICorDebugThread qui représente le thread dans lequel l’évaluation s’est terminée.</span><span class="sxs-lookup"><span data-stu-id="ac75a-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="ac75a-108">dans Pointeur vers un objet ICorDebugEval qui représente le code qui a effectué l’évaluation.</span><span class="sxs-lookup"><span data-stu-id="ac75a-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac75a-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ac75a-109">Requirements</span></span>  
 <span data-ttu-id="ac75a-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac75a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac75a-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac75a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac75a-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac75a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac75a-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac75a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac75a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac75a-114">See also</span></span>

- [<span data-ttu-id="ac75a-115">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="ac75a-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
