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
ms.openlocfilehash: f5af8e559b4fbfeb60530372185ca10104ade987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178847"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="04fed-102">ICorDebugHeapEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="04fed-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="04fed-103">Obtient le nombre spécifié de [cas COR_HEAPOBJECT](cor-heapobject-structure.md) qui contiennent des informations sur les objets sur le tas géré.</span><span class="sxs-lookup"><span data-stu-id="04fed-103">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04fed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04fed-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04fed-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="04fed-105">Parameters</span></span>  
 <span data-ttu-id="04fed-106">celt</span><span class="sxs-lookup"><span data-stu-id="04fed-106">celt</span></span>  
 <span data-ttu-id="04fed-107">[in] Nombre d'objets à récupérer.</span><span class="sxs-lookup"><span data-stu-id="04fed-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="04fed-108">objets</span><span class="sxs-lookup"><span data-stu-id="04fed-108">objects</span></span>  
 <span data-ttu-id="04fed-109">[out] Un tableau de pointeurs, chacun pointant vers un [objet COR_HEAPOBJECT](cor-heapobject-structure.md) qui fournit des informations sur un objet sur le tas géré.</span><span class="sxs-lookup"><span data-stu-id="04fed-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="04fed-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="04fed-110">pceltFetched</span></span>  
 <span data-ttu-id="04fed-111">[out] Un pointeur sur [COR_HEAPOBJECT](cor-heapobject-structure.md) le nombre d’objets `objects`COR_HEAPOBJECT effectivement retourné dans .</span><span class="sxs-lookup"><span data-stu-id="04fed-111">[out] A pointer to the number of [COR_HEAPOBJECT](cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="04fed-112">Cette valeur peut être `null` si `celt` est égal à 1.</span><span class="sxs-lookup"><span data-stu-id="04fed-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04fed-113">Notes </span><span class="sxs-lookup"><span data-stu-id="04fed-113">Remarks</span></span>  
 <span data-ttu-id="04fed-114">Le champ `COR_HEAPOBJECT.type` est l'identificateur d'une interface COM imbriquée avec comptage des références.</span><span class="sxs-lookup"><span data-stu-id="04fed-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="04fed-115">Cette référence doit être libérée par l'appelant d'`ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="04fed-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04fed-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="04fed-116">Requirements</span></span>  
 <span data-ttu-id="04fed-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04fed-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04fed-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04fed-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04fed-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04fed-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04fed-120">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04fed-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04fed-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04fed-121">See also</span></span>

- [<span data-ttu-id="04fed-122">ICorDebugHeapEnum, interface</span><span class="sxs-lookup"><span data-stu-id="04fed-122">ICorDebugHeapEnum Interface</span></span>](icordebugheapenum-interface.md)
- [<span data-ttu-id="04fed-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="04fed-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
