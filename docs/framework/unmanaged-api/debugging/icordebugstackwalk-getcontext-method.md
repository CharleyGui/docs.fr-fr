---
title: ICorDebugStackWalk::GetContext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f453e950a79b0f929ec8f813cc13eb2e01ab8c87
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760921"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="3ea96-102">ICorDebugStackWalk::GetContext, méthode</span><span class="sxs-lookup"><span data-stu-id="3ea96-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="3ea96-103">Retourne le contexte pour le frame actuel dans le [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="3ea96-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ea96-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ea96-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3ea96-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="3ea96-106">[in] Indicateurs qui spécifient le contenu demandé de la mémoire tampon de contexte (défini dans WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="3ea96-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="3ea96-107">[in] La taille allouée de la mémoire tampon de contexte.</span><span class="sxs-lookup"><span data-stu-id="3ea96-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="3ea96-108">[out] La taille réelle du contexte.</span><span class="sxs-lookup"><span data-stu-id="3ea96-108">[out] The actual size of the context.</span></span> <span data-ttu-id="3ea96-109">Cette valeur doit être inférieure ou égale à la taille de la mémoire tampon de contexte.</span><span class="sxs-lookup"><span data-stu-id="3ea96-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="3ea96-110">[out] Mémoire tampon de contexte.</span><span class="sxs-lookup"><span data-stu-id="3ea96-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ea96-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3ea96-111">Return Value</span></span>  
 <span data-ttu-id="3ea96-112">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="3ea96-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3ea96-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ea96-113">HRESULT</span></span>|<span data-ttu-id="3ea96-114">Description</span><span class="sxs-lookup"><span data-stu-id="3ea96-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ea96-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ea96-115">S_OK</span></span>|<span data-ttu-id="3ea96-116">Le contexte pour le frame actuel a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="3ea96-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="3ea96-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3ea96-117">E_FAIL</span></span>|<span data-ttu-id="3ea96-118">Le contexte n’a pas pu être retourné.</span><span class="sxs-lookup"><span data-stu-id="3ea96-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="3ea96-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="3ea96-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="3ea96-120">Mémoire tampon de contexte est trop petite.</span><span class="sxs-lookup"><span data-stu-id="3ea96-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="3ea96-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="3ea96-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="3ea96-122">Le pointeur de frame est déjà à la fin de la pile ; Par conséquent, aucun frame supplémentaires ne sont accessibles.</span><span class="sxs-lookup"><span data-stu-id="3ea96-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="3ea96-123">Exceptions</span><span class="sxs-lookup"><span data-stu-id="3ea96-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ea96-124">Notes</span><span class="sxs-lookup"><span data-stu-id="3ea96-124">Remarks</span></span>  
 <span data-ttu-id="3ea96-125">Étant donné que le déroulement restaure uniquement un sous-ensemble des registres, tels que les registres non volatils, le contexte peut différer l’état du Registre au moment de l’appel.</span><span class="sxs-lookup"><span data-stu-id="3ea96-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ea96-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3ea96-126">Requirements</span></span>  
 <span data-ttu-id="3ea96-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ea96-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ea96-128">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ea96-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ea96-129">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ea96-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ea96-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ea96-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea96-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ea96-131">See also</span></span>

- [<span data-ttu-id="3ea96-132">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3ea96-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3ea96-133">Débogage</span><span class="sxs-lookup"><span data-stu-id="3ea96-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
