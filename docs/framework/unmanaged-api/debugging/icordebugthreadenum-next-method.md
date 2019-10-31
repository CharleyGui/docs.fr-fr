---
title: ICorDebugThreadEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum::Next
helpviewer_keywords:
- ICorDebugThreadEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: f967c93d-9a7f-4aaf-99a1-a1317899ff3f
topic_type:
- apiref
ms.openlocfilehash: 0c455706b0d644d2444e9fbdf49c5a5d4f5295a9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122391"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="b6d5a-102">ICorDebugThreadEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="b6d5a-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="b6d5a-103">Obtient le nombre d’instances ICorDebugThread spécifiées à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="b6d5a-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6d5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6d5a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6d5a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b6d5a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b6d5a-106">dans Nombre d’instances de `ICorDebugThread` à récupérer.</span><span class="sxs-lookup"><span data-stu-id="b6d5a-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="b6d5a-107">à Tableau de pointeurs, chacun pointant vers un objet `ICorDebugThread` qui représente un thread.</span><span class="sxs-lookup"><span data-stu-id="b6d5a-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b6d5a-108">à Pointeur vers le nombre d’instances `ICorDebugThread` réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="b6d5a-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="b6d5a-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="b6d5a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6d5a-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="b6d5a-110">Requirements</span></span>  
 <span data-ttu-id="b6d5a-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6d5a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6d5a-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6d5a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6d5a-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6d5a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6d5a-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6d5a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
