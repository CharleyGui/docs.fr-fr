---
title: ICorDebugDataTarget::GetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2047929c52dbb7b0d780a4ea0f180bae48a3ce79
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750399"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="5e7bd-102">ICorDebugDataTarget::GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="5e7bd-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="5e7bd-103">Retourne le contexte actuel du thread pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="5e7bd-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e7bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e7bd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e7bd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e7bd-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="5e7bd-106">[in] L’identificateur du thread dont le contexte doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="5e7bd-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="5e7bd-107">L’identificateur est défini par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="5e7bd-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="5e7bd-108">[in] Une combinaison au niveau du bit des indicateurs dépend de la plateforme qui spécifient quelles parties du contexte doit être lue.</span><span class="sxs-lookup"><span data-stu-id="5e7bd-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="5e7bd-109">[in] Taille de `pContext`.</span><span class="sxs-lookup"><span data-stu-id="5e7bd-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="5e7bd-110">[out] La mémoire tampon où sera stocké le contexte du thread.</span><span class="sxs-lookup"><span data-stu-id="5e7bd-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e7bd-111">Notes</span><span class="sxs-lookup"><span data-stu-id="5e7bd-111">Remarks</span></span>  
 <span data-ttu-id="5e7bd-112">Sur les plateformes Windows, `pContext` doit être un `CONTEXT` structure (définie dans WinNT.h) qui est appropriée pour le type d’ordinateur spécifié par le [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5e7bd-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="5e7bd-113">`contextFlags` doit avoir les mêmes valeurs que le `ContextFlags` champ la `CONTEXT` structure.</span><span class="sxs-lookup"><span data-stu-id="5e7bd-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="5e7bd-114">Le `CONTEXT` structure est spécifique au processeur ; consultez le fichier WinNT.h pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="5e7bd-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e7bd-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5e7bd-115">Requirements</span></span>  
 <span data-ttu-id="5e7bd-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e7bd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e7bd-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e7bd-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e7bd-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e7bd-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e7bd-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e7bd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e7bd-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e7bd-120">See also</span></span>

- [<span data-ttu-id="5e7bd-121">ICorDebugDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="5e7bd-121">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="5e7bd-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5e7bd-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5e7bd-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="5e7bd-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
