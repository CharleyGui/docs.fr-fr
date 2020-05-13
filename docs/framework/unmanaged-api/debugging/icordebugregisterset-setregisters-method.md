---
title: ICorDebugRegisterSet::SetRegisters, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetRegisters
helpviewer_keywords:
- SetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::SetRegisters method [.NET Framework debugging]
ms.assetid: ac6244b9-54ba-475f-b72a-abed6afc46ec
topic_type:
- apiref
ms.openlocfilehash: eba86c09197aad6bac284c52fe164432e197c6f7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378261"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="e5553-102">ICorDebugRegisterSet::SetRegisters, méthode</span><span class="sxs-lookup"><span data-stu-id="e5553-102">ICorDebugRegisterSet::SetRegisters Method</span></span>
<span data-ttu-id="e5553-103">`SetRegisters`n’est pas implémenté dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5553-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="e5553-104">N'appelez pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="e5553-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5553-105">Utilisez les opérations de niveau supérieur telles que [ICorDebugILFrame :: SetIP](icordebugilframe-setip-method.md) ou [ICorDebugNativeFrame :: SetIP](icordebugnativeframe-setip-method.md).</span><span class="sxs-lookup"><span data-stu-id="e5553-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5553-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5553-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e5553-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e5553-107">Requirements</span></span>  
 <span data-ttu-id="e5553-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5553-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5553-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5553-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5553-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5553-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5553-111">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="e5553-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5553-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5553-112">See also</span></span>

- [<span data-ttu-id="e5553-113">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="e5553-113">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="e5553-114">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="e5553-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
