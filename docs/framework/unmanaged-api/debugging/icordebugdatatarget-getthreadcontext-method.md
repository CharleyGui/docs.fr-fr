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
ms.openlocfilehash: 79708aa5a2abcb8d7465f82a8beb918484c193b9
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976549"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a><span data-ttu-id="9d7cb-102">ICorDebugDataTarget::GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="9d7cb-102">ICorDebugDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="9d7cb-103">Retourne le contexte de thread actuel pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="9d7cb-103">Returns the current thread context for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d7cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d7cb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d7cb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d7cb-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="9d7cb-106">dans Identificateur du thread dont le contexte doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="9d7cb-106">[in] The identifier of the thread whose context is to be retrieved.</span></span> <span data-ttu-id="9d7cb-107">L’identificateur est défini par le système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="9d7cb-107">The identifier is defined by the operating system.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="9d7cb-108">dans Combinaison d’opérations de bits d’indicateurs dépendants de la plateforme qui indiquent les parties du contexte qui doivent être lues.</span><span class="sxs-lookup"><span data-stu-id="9d7cb-108">[in] A bitwise combination of platform-dependent flags that indicate which portions of the context should be read.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="9d7cb-109">[in] Taille de `pContext`.</span><span class="sxs-lookup"><span data-stu-id="9d7cb-109">[in] The size of `pContext`.</span></span>  
  
 `pContext`  
 <span data-ttu-id="9d7cb-110">à Mémoire tampon dans laquelle le contexte de thread sera stocké.</span><span class="sxs-lookup"><span data-stu-id="9d7cb-110">[out] The buffer where the thread context will be stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d7cb-111">Notes </span><span class="sxs-lookup"><span data-stu-id="9d7cb-111">Remarks</span></span>  
 <span data-ttu-id="9d7cb-112">Sur les plateformes `pContext` Windows, doit `CONTEXT` être une structure (définie dans Winnt. h) qui est appropriée pour le type d’ordinateur spécifié par la méthode [ICorDebugDataTarget :: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9d7cb-112">On Windows platforms, `pContext` must be a `CONTEXT` structure (defined in WinNT.h) that is appropriate for the machine type specified by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="9d7cb-113">`contextFlags`doit avoir les mêmes valeurs que le `ContextFlags` champ de la `CONTEXT` structure.</span><span class="sxs-lookup"><span data-stu-id="9d7cb-113">`contextFlags` must have the same values as the `ContextFlags` field of the `CONTEXT` structure.</span></span> <span data-ttu-id="9d7cb-114">La `CONTEXT` structure est spécifique au processeur ; Pour plus d’informations, consultez le fichier Winnt. h.</span><span class="sxs-lookup"><span data-stu-id="9d7cb-114">The `CONTEXT` structure is processor-specific; refer to the WinNT.h file for details.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d7cb-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9d7cb-115">Requirements</span></span>  
 <span data-ttu-id="9d7cb-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d7cb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d7cb-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d7cb-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d7cb-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d7cb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d7cb-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d7cb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d7cb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d7cb-120">See also</span></span>

- [<span data-ttu-id="9d7cb-121">ICorDebugDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="9d7cb-121">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="9d7cb-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9d7cb-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9d7cb-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="9d7cb-123">Debugging</span></span>](index.md)
