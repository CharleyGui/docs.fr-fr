---
title: ICorDebugStackWalk::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
ms.openlocfilehash: 497dda473e6510cfa31405b2066c63b1a70dd5e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677321"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="47680-102">ICorDebugStackWalk::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="47680-102">ICorDebugStackWalk::Next Method</span></span>

<span data-ttu-id="47680-103">Déplace l’objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) vers le frame suivant.</span><span class="sxs-lookup"><span data-stu-id="47680-103">Moves the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47680-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47680-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="47680-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="47680-105">Return Value</span></span>  

 <span data-ttu-id="47680-106">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="47680-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="47680-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="47680-107">HRESULT</span></span>|<span data-ttu-id="47680-108">Description</span><span class="sxs-lookup"><span data-stu-id="47680-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47680-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="47680-109">S_OK</span></span>|<span data-ttu-id="47680-110">Le runtime a été correctement déroulé au frame suivant (consultez la section Notes).</span><span class="sxs-lookup"><span data-stu-id="47680-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="47680-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="47680-111">E_FAIL</span></span>|<span data-ttu-id="47680-112">L' `ICorDebugStackWalk` objet n’a pas pu être avancé.</span><span class="sxs-lookup"><span data-stu-id="47680-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="47680-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="47680-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="47680-114">La fin de la pile a été atteinte à la suite de ce déroulement.</span><span class="sxs-lookup"><span data-stu-id="47680-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="47680-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="47680-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="47680-116">Le pointeur de frame est déjà à la fin de la pile ; par conséquent, il n’est pas possible d’accéder à des frames supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="47680-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="47680-117">Exceptions</span><span class="sxs-lookup"><span data-stu-id="47680-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47680-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="47680-118">Remarks</span></span>  

 <span data-ttu-id="47680-119">La `Next` méthode avance l' `ICorDebugStackWalk` objet jusqu’au frame appelant uniquement si le runtime peut dérouler le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="47680-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="47680-120">Dans le cas contraire, l’objet passe au frame suivant que le runtime est en mesure de dérouler.</span><span class="sxs-lookup"><span data-stu-id="47680-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47680-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="47680-121">Requirements</span></span>  

 <span data-ttu-id="47680-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47680-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47680-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47680-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47680-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47680-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47680-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47680-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47680-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47680-126">See also</span></span>

- [<span data-ttu-id="47680-127">ICorDebugStackWalk, interface</span><span class="sxs-lookup"><span data-stu-id="47680-127">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="47680-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="47680-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="47680-129">Débogage</span><span class="sxs-lookup"><span data-stu-id="47680-129">Debugging</span></span>](index.md)
