---
title: ICorDebugMutableDataTarget::SetThreadContext, méthode
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6629af393eeadb68292f8f2360ecb60c09a0cd03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764613"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="983b2-102">ICorDebugMutableDataTarget::SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="983b2-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="983b2-103">Définit le contexte (valeurs de registre) d'un thread.</span><span class="sxs-lookup"><span data-stu-id="983b2-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="983b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="983b2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="983b2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="983b2-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="983b2-106">[in] Identificateur de thread défini par le système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="983b2-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="983b2-107">[in] Taille de la mémoire tampon `pContext` à écrire.</span><span class="sxs-lookup"><span data-stu-id="983b2-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="983b2-108">[in] Pointeur vers les octets à écrire.</span><span class="sxs-lookup"><span data-stu-id="983b2-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="983b2-109">Notes</span><span class="sxs-lookup"><span data-stu-id="983b2-109">Remarks</span></span>  
 <span data-ttu-id="983b2-110">La méthode `SetThreadContext` met à jour le contexte actuel du thread spécifié par l'argument `dwThreadID` défini par le système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="983b2-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="983b2-111">Le format de l’enregistrement de contexte est déterminé par la plateforme indiquée par le [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="983b2-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="983b2-112">Sur Windows, il s’agit d’un [contexte](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) structure.</span><span class="sxs-lookup"><span data-stu-id="983b2-112">On Windows, this is a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="983b2-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="983b2-113">Requirements</span></span>  
 <span data-ttu-id="983b2-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="983b2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="983b2-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="983b2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="983b2-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="983b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="983b2-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="983b2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="983b2-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="983b2-118">See also</span></span>

- [<span data-ttu-id="983b2-119">ICorDebugMutableDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="983b2-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="983b2-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="983b2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
