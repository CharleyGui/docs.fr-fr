---
title: ICorDebugStackWalk::SetContext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
ms.openlocfilehash: 23ad8882ad97e5ceaeb690dfae08a6be55b85f64
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791858"
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="92b5f-102">ICorDebugStackWalk::SetContext, méthode</span><span class="sxs-lookup"><span data-stu-id="92b5f-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="92b5f-103">Affecte au contexte actuel de l’objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) un contexte valide pour le thread.</span><span class="sxs-lookup"><span data-stu-id="92b5f-103">Sets the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92b5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92b5f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92b5f-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="92b5f-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="92b5f-106">dans Indicateur [CorDebugSetContextFlag,](cordebugsetcontextflag-enumeration.md) qui indique si le contexte provient du frame actif sur la pile ou d’un contexte obtenu en déroulant la pile.</span><span class="sxs-lookup"><span data-stu-id="92b5f-106">[in] A [CorDebugSetContextFlag](cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="92b5f-107">dans Taille allouée de la mémoire tampon de `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="92b5f-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="92b5f-108">dans Mémoire tampon de `CONTEXT`.</span><span class="sxs-lookup"><span data-stu-id="92b5f-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92b5f-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="92b5f-109">Return Value</span></span>  
 <span data-ttu-id="92b5f-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="92b5f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="92b5f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92b5f-111">HRESULT</span></span>|<span data-ttu-id="92b5f-112">Description</span><span class="sxs-lookup"><span data-stu-id="92b5f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92b5f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="92b5f-113">S_OK</span></span>|<span data-ttu-id="92b5f-114">Le contexte de l’objet `ICorDebugStackWalk` a été correctement défini.</span><span class="sxs-lookup"><span data-stu-id="92b5f-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="92b5f-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="92b5f-115">E_FAIL</span></span>|<span data-ttu-id="92b5f-116">Le contexte de l’objet `ICorDebugStackWalk` n’a pas été défini.</span><span class="sxs-lookup"><span data-stu-id="92b5f-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="92b5f-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="92b5f-117">E_INVALIDARG</span></span>|<span data-ttu-id="92b5f-118">Le contexte a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="92b5f-118">The context is null.</span></span>|  
|<span data-ttu-id="92b5f-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="92b5f-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="92b5f-120">La mémoire tampon de contexte est trop petite.</span><span class="sxs-lookup"><span data-stu-id="92b5f-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="92b5f-121">Exceptions</span><span class="sxs-lookup"><span data-stu-id="92b5f-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92b5f-122">Notes</span><span class="sxs-lookup"><span data-stu-id="92b5f-122">Remarks</span></span>  
 <span data-ttu-id="92b5f-123">Cette méthode ne modifie pas le contexte actuel du thread.</span><span class="sxs-lookup"><span data-stu-id="92b5f-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="92b5f-124">L’activation d’un contexte non valide dans le contexte actuel peut entraîner des résultats imprévisibles de l’Explorateur de pile.</span><span class="sxs-lookup"><span data-stu-id="92b5f-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="92b5f-125">Vous pouvez récupérer une copie au niveau du bit exacte de ce contexte en appelant immédiatement la méthode [ICorDebugStackWalk :: GetContext](icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="92b5f-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92b5f-126">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="92b5f-126">Requirements</span></span>  
 <span data-ttu-id="92b5f-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92b5f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92b5f-128">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92b5f-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92b5f-129">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92b5f-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92b5f-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92b5f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b5f-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92b5f-131">See also</span></span>

- [<span data-ttu-id="92b5f-132">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="92b5f-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="92b5f-133">Débogage</span><span class="sxs-lookup"><span data-stu-id="92b5f-133">Debugging</span></span>](index.md)
