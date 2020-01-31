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
ms.openlocfilehash: 8137d5477b75b864e223852cf524ac8c5b6c0f2b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792089"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="323b1-102">ICorDebugRegisterSet::GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="323b1-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="323b1-103">Obtient le contexte du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="323b1-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="323b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="323b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="323b1-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="323b1-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="323b1-106">dans Taille, en octets, du tableau de `context`.</span><span class="sxs-lookup"><span data-stu-id="323b1-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="323b1-107">[in, out] Tableau d’octets qui composent la structure de `CONTEXT` Win32 pour la plateforme actuelle.</span><span class="sxs-lookup"><span data-stu-id="323b1-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="323b1-108">Notes</span><span class="sxs-lookup"><span data-stu-id="323b1-108">Remarks</span></span>  
 <span data-ttu-id="323b1-109">Le débogueur doit appeler cette fonction au lieu de la fonction `GetThreadContext` Win32, car le thread peut être dans un État « détourné » dans lequel son contexte a été modifié temporairement.</span><span class="sxs-lookup"><span data-stu-id="323b1-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="323b1-110">Les données retournées sont une structure de `CONTEXT` Win32 pour la plateforme actuelle.</span><span class="sxs-lookup"><span data-stu-id="323b1-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="323b1-111">Pour les frames non-feuilles, les clients doivent vérifier quels registres sont valides à l’aide de [ICorDebugRegisterSet :: GetRegistersAvailable,](icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="323b1-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="323b1-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="323b1-112">Requirements</span></span>  
 <span data-ttu-id="323b1-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="323b1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="323b1-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="323b1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="323b1-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="323b1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="323b1-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="323b1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="323b1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="323b1-117">See also</span></span>

- [<span data-ttu-id="323b1-118">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="323b1-118">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="323b1-119">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="323b1-119">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
