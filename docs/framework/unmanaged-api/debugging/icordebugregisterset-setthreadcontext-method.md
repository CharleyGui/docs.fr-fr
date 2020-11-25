---
title: ICorDebugRegisterSet::SetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
ms.openlocfilehash: 66e8cf3f73e92f58765b1fa98b3eef11b976094c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712272"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="fc13c-102">ICorDebugRegisterSet::SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="fc13c-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>

<span data-ttu-id="fc13c-103">`SetThreadContext` n’est pas implémenté dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc13c-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="fc13c-104">N'appelez pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="fc13c-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc13c-105">Utilisez l’opération de niveau supérieur [ICorDebugNativeFrame :: SetIP](icordebugnativeframe-setip-method.md) pour définir le contexte d’un thread.</span><span class="sxs-lookup"><span data-stu-id="fc13c-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc13c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="fc13c-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="fc13c-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fc13c-107">Requirements</span></span>  

 <span data-ttu-id="fc13c-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc13c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc13c-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc13c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc13c-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc13c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc13c-111">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="fc13c-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc13c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc13c-112">See also</span></span>

- [<span data-ttu-id="fc13c-113">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="fc13c-113">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="fc13c-114">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="fc13c-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
