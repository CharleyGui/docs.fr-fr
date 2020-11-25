---
title: ICorDebugRegisterSet2::SetRegisters, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::SetRegisters
helpviewer_keywords:
- ICorDebugRegisterSet2::SetRegisters method [.NET Framework debugging]
- SetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: fe0ac7e7-c9e1-4ec1-9f4e-1c56d63d73ac
topic_type:
- apiref
ms.openlocfilehash: 53660a5b10858632dffc5b31c290e9cb98d634c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712298"
---
# <a name="icordebugregisterset2setregisters-method"></a><span data-ttu-id="0914a-102">ICorDebugRegisterSet2::SetRegisters, méthode</span><span class="sxs-lookup"><span data-stu-id="0914a-102">ICorDebugRegisterSet2::SetRegisters Method</span></span>

<span data-ttu-id="0914a-103">`SetRegisters` n’est pas implémenté dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0914a-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="0914a-104">N'appelez pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="0914a-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0914a-105">Utilisez les opérations de niveau supérieur telles que [ICorDebugILFrame :: SetIP](icordebugilframe-setip-method.md) ou [ICorDebugNativeFrame :: SetIP](icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="0914a-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0914a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0914a-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0914a-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0914a-107">Requirements</span></span>  

 <span data-ttu-id="0914a-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0914a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0914a-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0914a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0914a-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0914a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0914a-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0914a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0914a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0914a-112">See also</span></span>

- [<span data-ttu-id="0914a-113">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="0914a-113">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="0914a-114">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="0914a-114">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
