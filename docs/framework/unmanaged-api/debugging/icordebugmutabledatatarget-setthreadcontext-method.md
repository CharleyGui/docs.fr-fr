---
title: ICorDebugMutableDataTarget::SetThreadContext, méthode
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 558a1ee2eb0ac06213c2ebcebbd5595b69ecc43e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695708"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="4e909-102">ICorDebugMutableDataTarget::SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="4e909-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>

<span data-ttu-id="4e909-103">Définit le contexte (valeurs de registre) d'un thread.</span><span class="sxs-lookup"><span data-stu-id="4e909-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e909-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e909-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e909-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4e909-105">Parameters</span></span>  

 `dwThreadID`  
 <span data-ttu-id="4e909-106">[in] Identificateur de thread défini par le système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="4e909-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="4e909-107">[in] Taille de la mémoire tampon `pContext` à écrire.</span><span class="sxs-lookup"><span data-stu-id="4e909-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="4e909-108">[in] Pointeur vers les octets à écrire.</span><span class="sxs-lookup"><span data-stu-id="4e909-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e909-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="4e909-109">Remarks</span></span>  

 <span data-ttu-id="4e909-110">La méthode `SetThreadContext` met à jour le contexte actuel du thread spécifié par l'argument `dwThreadID` défini par le système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="4e909-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="4e909-111">Le format de l’enregistrement de contexte est déterminé par la plateforme indiquée par la méthode [ICorDebugDataTarget :: GetPlatform](icordebugdatatarget-getplatform-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4e909-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="4e909-112">Sur Windows, il s’agit d’une structure de [contexte](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .</span><span class="sxs-lookup"><span data-stu-id="4e909-112">On Windows, this is a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e909-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4e909-113">Requirements</span></span>  

 <span data-ttu-id="4e909-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e909-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e909-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e909-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e909-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e909-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e909-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e909-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e909-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e909-118">See also</span></span>

- [<span data-ttu-id="4e909-119">ICorDebugMutableDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="4e909-119">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="4e909-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4e909-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
