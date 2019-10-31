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
ms.openlocfilehash: 8731b57206f7987efc2498a5abe62295cd1cfae5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131326"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="aae2c-102">ICorDebugRegisterSet::SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="aae2c-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="aae2c-103">`SetThreadContext` n’est pas implémenté dans la version .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="aae2c-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="aae2c-104">N'appelez pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="aae2c-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aae2c-105">Utilisez l’opération de niveau supérieur [ICorDebugNativeFrame :: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) pour définir le contexte d’un thread.</span><span class="sxs-lookup"><span data-stu-id="aae2c-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aae2c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aae2c-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="aae2c-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="aae2c-107">Requirements</span></span>  
 <span data-ttu-id="aae2c-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aae2c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aae2c-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aae2c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aae2c-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aae2c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aae2c-111">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="aae2c-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aae2c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aae2c-112">See also</span></span>

- [<span data-ttu-id="aae2c-113">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="aae2c-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="aae2c-114">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="aae2c-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
