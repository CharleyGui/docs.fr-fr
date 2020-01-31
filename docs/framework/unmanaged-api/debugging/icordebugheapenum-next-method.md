---
title: ICorDebugHeapEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: 2c84112984e9cb7dec2a492ac16af00e14770806
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782493"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="0d177-102">ICorDebugHeapEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="0d177-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="0d177-103">Obtient le nombre spécifié d’instances [COR_HEAPOBJECT](cor-heapobject-structure.md) qui contiennent des informations sur les objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="0d177-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d177-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d177-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d177-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="0d177-105">Parameters</span></span>  
 <span data-ttu-id="0d177-106">celt</span><span class="sxs-lookup"><span data-stu-id="0d177-106">celt</span></span>  
 <span data-ttu-id="0d177-107">[in] Nombre d'objets à récupérer.</span><span class="sxs-lookup"><span data-stu-id="0d177-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="0d177-108">Windows Azure</span><span class="sxs-lookup"><span data-stu-id="0d177-108">objects</span></span>  
 <span data-ttu-id="0d177-109">à Tableau de pointeurs, chacun pointant vers un objet [COR_HEAPOBJECT](cor-heapobject-structure.md) qui fournit des informations sur un objet sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="0d177-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="0d177-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="0d177-110">pceltFetched</span></span>  
 <span data-ttu-id="0d177-111">à Pointeur vers le nombre d’objets [COR_HEAPOBJECT](cor-heapobject-structure.md) réellement retournés dans `objects`.</span><span class="sxs-lookup"><span data-stu-id="0d177-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="0d177-112">Cette valeur peut être `null` si `celt` est égal à 1.</span><span class="sxs-lookup"><span data-stu-id="0d177-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d177-113">Notes</span><span class="sxs-lookup"><span data-stu-id="0d177-113">Remarks</span></span>  
 <span data-ttu-id="0d177-114">Le champ `COR_HEAPOBJECT.type` est l'identificateur d'une interface COM imbriquée avec comptage des références.</span><span class="sxs-lookup"><span data-stu-id="0d177-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="0d177-115">Cette référence doit être libérée par l'appelant d'`ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="0d177-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d177-116">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="0d177-116">Requirements</span></span>  
 <span data-ttu-id="0d177-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d177-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d177-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d177-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d177-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d177-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d177-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d177-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d177-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d177-121">See also</span></span>

- [<span data-ttu-id="0d177-122">ICorDebugHeapEnum, interface</span><span class="sxs-lookup"><span data-stu-id="0d177-122">ICorDebugHeapEnum Interface</span></span>](icordebugheapenum-interface.md)
- [<span data-ttu-id="0d177-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0d177-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
