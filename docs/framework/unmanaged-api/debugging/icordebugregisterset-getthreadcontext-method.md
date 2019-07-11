---
title: ICorDebugRegisterSet::GetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef7619316cae46df350bd75a2c6838828f7e9c82
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747184"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="a39dc-102">ICorDebugRegisterSet::GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="a39dc-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="a39dc-103">Obtient le contexte du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="a39dc-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a39dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a39dc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a39dc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a39dc-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="a39dc-106">[in] La taille, en octets, de la `context` tableau.</span><span class="sxs-lookup"><span data-stu-id="a39dc-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="a39dc-107">[in, out] Un tableau d’octets qui composent le Win32 `CONTEXT` structure pour la plateforme actuelle.</span><span class="sxs-lookup"><span data-stu-id="a39dc-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a39dc-108">Notes</span><span class="sxs-lookup"><span data-stu-id="a39dc-108">Remarks</span></span>  
 <span data-ttu-id="a39dc-109">Le débogueur doit appeler cette fonction au lieu de Win32 `GetThreadContext` fonctionner, car le thread peut être dans un état « infiltré » où son contexte a été changé temporairement.</span><span class="sxs-lookup"><span data-stu-id="a39dc-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="a39dc-110">Les données retournées sont un Win32 `CONTEXT` structure pour la plateforme actuelle.</span><span class="sxs-lookup"><span data-stu-id="a39dc-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="a39dc-111">Pour les frames, les clients doivent vérifier les registres qui sont valides à l’aide de [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="a39dc-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a39dc-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a39dc-112">Requirements</span></span>  
 <span data-ttu-id="a39dc-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a39dc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a39dc-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a39dc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a39dc-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a39dc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a39dc-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a39dc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a39dc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a39dc-117">See also</span></span>

- [<span data-ttu-id="a39dc-118">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="a39dc-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="a39dc-119">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="a39dc-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
