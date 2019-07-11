---
title: ICorDebugChainEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4e8b1a76bcc56424e61991d36c94c5f2dfab8aa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745604"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="dda2b-102">ICorDebugChainEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="dda2b-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="dda2b-103">Obtient le nombre spécifié d’instances ICorDebugChain à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="dda2b-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dda2b-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dda2b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dda2b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="dda2b-106">[in] Le nombre de `ICorDebugChain` instances à récupérer.</span><span class="sxs-lookup"><span data-stu-id="dda2b-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="dda2b-107">[out] Un tableau de pointeurs, chacun d’eux pointe vers un `ICorDebugChain` objet qui représente une chaîne.</span><span class="sxs-lookup"><span data-stu-id="dda2b-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="dda2b-108">[out] Un pointeur vers le nombre de `ICorDebugChain` instances réellement retournés.</span><span class="sxs-lookup"><span data-stu-id="dda2b-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="dda2b-109">Cette valeur peut être null si `celt` fait partie.</span><span class="sxs-lookup"><span data-stu-id="dda2b-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dda2b-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dda2b-110">Requirements</span></span>  
 <span data-ttu-id="dda2b-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dda2b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dda2b-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dda2b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dda2b-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dda2b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dda2b-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dda2b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
