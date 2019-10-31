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
ms.openlocfilehash: 3c11a0547ad5acc5613324d7e9d7439d44549dbc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125810"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="9d65c-102">ICorDebugChainEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="9d65c-102">ICorDebugChainEnum::Next Method</span></span>
<span data-ttu-id="9d65c-103">Obtient le nombre spécifié d’instances ICorDebugChain de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="9d65c-103">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d65c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d65c-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d65c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d65c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9d65c-106">dans Nombre d’instances de `ICorDebugChain` à récupérer.</span><span class="sxs-lookup"><span data-stu-id="9d65c-106">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="9d65c-107">à Tableau de pointeurs, chacun pointant vers un objet `ICorDebugChain` représentant une chaîne.</span><span class="sxs-lookup"><span data-stu-id="9d65c-107">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9d65c-108">à Pointeur vers le nombre d’instances `ICorDebugChain` réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="9d65c-108">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="9d65c-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="9d65c-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d65c-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="9d65c-110">Requirements</span></span>  
 <span data-ttu-id="9d65c-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d65c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d65c-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d65c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d65c-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d65c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d65c-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d65c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
