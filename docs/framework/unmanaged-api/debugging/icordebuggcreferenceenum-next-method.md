---
title: ICorDebugGCReferenceEnum::Next, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
ms.openlocfilehash: d87f414e9dfd05a519b60efc7ecdd5328a6dd86f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178866"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="47581-102">ICorDebugGCReferenceEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="47581-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="47581-103">Obtient le nombre spécifié de [cas COR_GC_REFERENCE](cor-gc-reference-structure.md) qui contiennent des informations sur les objets qui seront collectés à ordures.</span><span class="sxs-lookup"><span data-stu-id="47581-103">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47581-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47581-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47581-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="47581-105">Parameters</span></span>  
 <span data-ttu-id="47581-106">celt</span><span class="sxs-lookup"><span data-stu-id="47581-106">celt</span></span>  
 <span data-ttu-id="47581-107">[dans] Le nombre de racines à récupérer.</span><span class="sxs-lookup"><span data-stu-id="47581-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="47581-108">Racines</span><span class="sxs-lookup"><span data-stu-id="47581-108">roots</span></span>  
 <span data-ttu-id="47581-109">[out] Un tableau de pointeurs, chacun pointant vers un [objet COR_GC_REFERENCE](cor-gc-reference-structure.md) qui représente la racine d’un objet à collecter des ordures.</span><span class="sxs-lookup"><span data-stu-id="47581-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="47581-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="47581-110">pceltFetched</span></span>  
 <span data-ttu-id="47581-111">[out] Un pointeur sur le nombre d’objets [COR_GC_REFERENCE](cor-gc-reference-structure.md) effectivement retourné dans `roots`.</span><span class="sxs-lookup"><span data-stu-id="47581-111">[out] A pointer to the number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="47581-112">Cette valeur peut être `null` si `celt` est égal à 1.</span><span class="sxs-lookup"><span data-stu-id="47581-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47581-113">Notes </span><span class="sxs-lookup"><span data-stu-id="47581-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47581-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="47581-114">Requirements</span></span>  
 <span data-ttu-id="47581-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47581-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47581-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47581-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47581-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47581-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47581-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47581-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47581-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47581-119">See also</span></span>

- [<span data-ttu-id="47581-120">ICorDebugGCReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="47581-120">ICorDebugGCReferenceEnum Interface</span></span>](icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="47581-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="47581-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
