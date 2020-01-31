---
title: CorGCReferenceType, énumération
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
ms.openlocfilehash: 17d47b6242bb12ff5ca3cfbde3e4ec183b9c19fc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793875"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="53def-102">CorGCReferenceType, énumération</span><span class="sxs-lookup"><span data-stu-id="53def-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="53def-103">Identifie la source d'un objet pour lequel l'espace occupé en mémoire peut être récupéré.</span><span class="sxs-lookup"><span data-stu-id="53def-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53def-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53def-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a><span data-ttu-id="53def-105">Members</span><span class="sxs-lookup"><span data-stu-id="53def-105">Members</span></span>  
  
|<span data-ttu-id="53def-106">Nom du membre</span><span class="sxs-lookup"><span data-stu-id="53def-106">Member name</span></span>|<span data-ttu-id="53def-107">Description</span><span class="sxs-lookup"><span data-stu-id="53def-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="53def-108">Handle à une référence forte tiré de la table de handles d'objets.</span><span class="sxs-lookup"><span data-stu-id="53def-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="53def-109">Handle d’une référence forte épinglée de la table de handles d’objets.</span><span class="sxs-lookup"><span data-stu-id="53def-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="53def-110">Handle d’une référence faible à partir de la table de handles d’objets.</span><span class="sxs-lookup"><span data-stu-id="53def-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="53def-111">Handle d’un objet de référence faible à partir de la table de handles d’objets.</span><span class="sxs-lookup"><span data-stu-id="53def-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="53def-112">Handle d’un objet compté en référence à partir de la table de handles d’objets.</span><span class="sxs-lookup"><span data-stu-id="53def-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="53def-113">Handle vers un objet dépendant de la table de handles d’objets.</span><span class="sxs-lookup"><span data-stu-id="53def-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="53def-114">Objet épinglé asynchrone tiré de la table de handles d'objets.</span><span class="sxs-lookup"><span data-stu-id="53def-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="53def-115">Handle fort qui conserve une taille approximative de la fermeture collective de tous les objets et racines d’objets au moment du Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="53def-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="53def-116">Référence à partir de la pile managée.</span><span class="sxs-lookup"><span data-stu-id="53def-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="53def-117">Référence à partir de la file d’attente du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="53def-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="53def-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="53def-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="53def-119">Retourne uniquement les références fortes de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="53def-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="53def-120">Cette valeur est utilisée uniquement par la méthode [ICorDebugProcess5 :: enumeratehandles,](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="53def-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="53def-121">Retourne uniquement les références faibles de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="53def-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="53def-122">Cette valeur est utilisée uniquement par la méthode [ICorDebugProcess5 :: enumeratehandles,](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="53def-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="53def-123">Retourne toutes les références de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="53def-123">Return all references from the handle table.</span></span> <span data-ttu-id="53def-124">Cette valeur est utilisée uniquement par la méthode [ICorDebugProcess5 :: enumeratehandles,](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="53def-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53def-125">Notes</span><span class="sxs-lookup"><span data-stu-id="53def-125">Remarks</span></span>  
 <span data-ttu-id="53def-126">L’énumération `CorGCReferenceType` est utilisée comme suit :</span><span class="sxs-lookup"><span data-stu-id="53def-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
- <span data-ttu-id="53def-127">En tant que valeur du champ `type` de la structure [COR_GC_REFERENCE](cor-gc-reference-structure.md) , elle indique la source d’une référence ou d’un handle.</span><span class="sxs-lookup"><span data-stu-id="53def-127">As the value of the `type` field of the [COR_GC_REFERENCE](cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
- <span data-ttu-id="53def-128">En tant qu’argument `types` de la méthode [ICorDebugProcess5 :: enumeratehandles,](icordebugprocess5-enumeratehandles-method.md) , il spécifie les types de handles à inclure dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="53def-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53def-129">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="53def-129">Requirements</span></span>  
 <span data-ttu-id="53def-130">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53def-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53def-131">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53def-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53def-132">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53def-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53def-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53def-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53def-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53def-134">See also</span></span>

- [<span data-ttu-id="53def-135">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="53def-135">Debugging Enumerations</span></span>](debugging-enumerations.md)
