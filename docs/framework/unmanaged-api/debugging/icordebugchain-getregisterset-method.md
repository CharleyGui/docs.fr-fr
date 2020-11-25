---
title: ICorDebugChain::GetRegisterSet, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetRegisterSet
helpviewer_keywords:
- ICorDebugChain::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: bc4288b6-3331-4ae3-990d-e1d6e62ecb67
topic_type:
- apiref
ms.openlocfilehash: a3f02af1a0de9fcd7b3db1e49ef0d78af3395d2f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719656"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="9692f-102">ICorDebugChain::GetRegisterSet, méthode</span><span class="sxs-lookup"><span data-stu-id="9692f-102">ICorDebugChain::GetRegisterSet Method</span></span>

<span data-ttu-id="9692f-103">Obtient le Registre défini pour la partie active de cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="9692f-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9692f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9692f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9692f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9692f-105">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="9692f-106">à Pointeur vers l’adresse d’un objet [ICorDebugRegisterSet](icordebugregisterset-interface.md) qui représente le jeu de registres pour la partie active de cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="9692f-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9692f-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9692f-107">Requirements</span></span>  

 <span data-ttu-id="9692f-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9692f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9692f-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9692f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9692f-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9692f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9692f-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9692f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
