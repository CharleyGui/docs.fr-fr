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
ms.openlocfilehash: 66c10e5ecdd1610ee170b412c2778b8117d6c407
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131301"
---
# <a name="icordebugregisterset2setregisters-method"></a><span data-ttu-id="3351e-102">ICorDebugRegisterSet2::SetRegisters, méthode</span><span class="sxs-lookup"><span data-stu-id="3351e-102">ICorDebugRegisterSet2::SetRegisters Method</span></span>
<span data-ttu-id="3351e-103">`SetRegisters` n’est pas implémenté dans la version .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="3351e-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3351e-104">N'appelez pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="3351e-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3351e-105">Utilisez les opérations de niveau supérieur telles que [ICorDebugILFrame :: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) ou [ICorDebugNativeFrame :: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="3351e-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3351e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3351e-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3351e-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="3351e-107">Requirements</span></span>  
 <span data-ttu-id="3351e-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3351e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3351e-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3351e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3351e-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3351e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3351e-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3351e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3351e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3351e-112">See also</span></span>

- [<span data-ttu-id="3351e-113">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="3351e-113">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="3351e-114">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="3351e-114">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
