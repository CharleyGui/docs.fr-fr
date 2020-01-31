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
ms.openlocfilehash: 3a8e967a3ecc452ebda08872d8bcd9e9d08c766f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777691"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="52eab-102">ICorDebugGCReferenceEnum::Next, méthode</span><span class="sxs-lookup"><span data-stu-id="52eab-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="52eab-103">Obtient le nombre spécifié d’instances de [COR_GC_REFERENCE](cor-gc-reference-structure.md) qui contiennent des informations sur les objets qui feront l’objet d’un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="52eab-103">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52eab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52eab-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52eab-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="52eab-105">Parameters</span></span>  
 <span data-ttu-id="52eab-106">celt</span><span class="sxs-lookup"><span data-stu-id="52eab-106">celt</span></span>  
 <span data-ttu-id="52eab-107">dans Nombre de racines à récupérer.</span><span class="sxs-lookup"><span data-stu-id="52eab-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="52eab-108">digne</span><span class="sxs-lookup"><span data-stu-id="52eab-108">roots</span></span>  
 <span data-ttu-id="52eab-109">à Tableau de pointeurs, chacun pointant vers un objet [COR_GC_REFERENCE](cor-gc-reference-structure.md) qui représente la racine d’un objet qui doit faire l’objet d’un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="52eab-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="52eab-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="52eab-110">pceltFetched</span></span>  
 <span data-ttu-id="52eab-111">à Pointeur vers le nombre d’objets [COR_GC_REFERENCE](cor-gc-reference-structure.md) réellement retournés dans `roots`.</span><span class="sxs-lookup"><span data-stu-id="52eab-111">[out] A pointer to the number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="52eab-112">Cette valeur peut être `null` si `celt` est égal à 1.</span><span class="sxs-lookup"><span data-stu-id="52eab-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52eab-113">Notes</span><span class="sxs-lookup"><span data-stu-id="52eab-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52eab-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="52eab-114">Requirements</span></span>  
 <span data-ttu-id="52eab-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52eab-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52eab-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52eab-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52eab-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52eab-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52eab-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52eab-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52eab-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52eab-119">See also</span></span>

- [<span data-ttu-id="52eab-120">ICorDebugGCReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="52eab-120">ICorDebugGCReferenceEnum Interface</span></span>](icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="52eab-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="52eab-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
