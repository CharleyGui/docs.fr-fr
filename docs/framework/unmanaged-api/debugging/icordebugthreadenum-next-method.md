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
ms.openlocfilehash: c025afac1b53b23636a6160a475704011999d434
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379042"
---
# <a name="icordebugthreadenumnext-method"></a><span data-ttu-id="b85ce-102">ICorDebugThreadEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="b85ce-102">ICorDebugThreadEnum::Next Method</span></span>
<span data-ttu-id="b85ce-103">Obtient le nombre d’instances ICorDebugThread spécifiées à partir de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="b85ce-103">Gets the number of specified ICorDebugThread instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b85ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b85ce-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugThread *threads[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b85ce-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b85ce-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b85ce-106">dans Nombre d' `ICorDebugThread` instances à récupérer.</span><span class="sxs-lookup"><span data-stu-id="b85ce-106">[in] The number of `ICorDebugThread` instances to be retrieved.</span></span>  
  
 `threads`  
 <span data-ttu-id="b85ce-107">à Tableau de pointeurs, chacun pointant vers un `ICorDebugThread` objet qui représente un thread.</span><span class="sxs-lookup"><span data-stu-id="b85ce-107">[out] An array of pointers, each of which points to an `ICorDebugThread` object that represents a thread.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b85ce-108">à Pointeur vers le nombre d' `ICorDebugThread` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="b85ce-108">[out] Pointer to the number of `ICorDebugThread` instances actually returned.</span></span> <span data-ttu-id="b85ce-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="b85ce-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b85ce-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b85ce-110">Requirements</span></span>  
 <span data-ttu-id="b85ce-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b85ce-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b85ce-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b85ce-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b85ce-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b85ce-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b85ce-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b85ce-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
