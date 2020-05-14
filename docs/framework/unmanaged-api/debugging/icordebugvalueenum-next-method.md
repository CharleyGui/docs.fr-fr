---
title: ICorDebugValueEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
ms.openlocfilehash: db1721fed6414310556ceac493275e069a781ac8
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397146"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="aafbd-102">ICorDebugValueEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="aafbd-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="aafbd-103">Obtient le nombre spécifié d’instances « ICorDebugValue » de l’énumération, en commençant à la position actuelle.</span><span class="sxs-lookup"><span data-stu-id="aafbd-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aafbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aafbd-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aafbd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aafbd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="aafbd-106">dans Nombre d' `ICorDebugValue` instances à récupérer.</span><span class="sxs-lookup"><span data-stu-id="aafbd-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="aafbd-107">à Tableau de pointeurs, chacun pointant vers un `ICorDebugValue` objet.</span><span class="sxs-lookup"><span data-stu-id="aafbd-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="aafbd-108">à Pointeur vers le nombre d' `ICorDebugValue` instances réellement retournées.</span><span class="sxs-lookup"><span data-stu-id="aafbd-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="aafbd-109">Cette valeur peut être null si `celt` est un.</span><span class="sxs-lookup"><span data-stu-id="aafbd-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aafbd-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="aafbd-110">Requirements</span></span>  
 <span data-ttu-id="aafbd-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aafbd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aafbd-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aafbd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aafbd-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aafbd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aafbd-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aafbd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aafbd-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aafbd-115">See also</span></span>
