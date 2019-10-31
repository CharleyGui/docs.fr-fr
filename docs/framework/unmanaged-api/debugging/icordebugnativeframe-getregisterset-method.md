---
title: ICorDebugNativeFrame::GetRegisterSet, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetRegisterSet
helpviewer_keywords:
- ICorDebugNativeFrame::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 6f309b5f-5556-4f1e-b1dd-4fe97fc81d01
topic_type:
- apiref
ms.openlocfilehash: ac7601f89c125cecbfbd212118420a800f495742
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096813"
---
# <a name="icordebugnativeframegetregisterset-method"></a><span data-ttu-id="533e5-102">ICorDebugNativeFrame::GetRegisterSet, méthode</span><span class="sxs-lookup"><span data-stu-id="533e5-102">ICorDebugNativeFrame::GetRegisterSet Method</span></span>
<span data-ttu-id="533e5-103">Obtient le Registre défini pour ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="533e5-103">Gets the register set for this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="533e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="533e5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="533e5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="533e5-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="533e5-106">à Pointeur vers l’adresse d’un objet [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) qui représente le jeu de registres pour ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="533e5-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for this stack frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="533e5-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="533e5-107">Requirements</span></span>  
 <span data-ttu-id="533e5-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="533e5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="533e5-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="533e5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="533e5-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="533e5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="533e5-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="533e5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="533e5-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="533e5-112">See also</span></span>
