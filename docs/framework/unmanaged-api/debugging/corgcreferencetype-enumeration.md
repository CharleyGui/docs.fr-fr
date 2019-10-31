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
ms.openlocfilehash: eafae181c74d9f3842f7f0d547bcccbbb28c09e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132120"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="59068-102">CorGCReferenceType, énumération</span><span class="sxs-lookup"><span data-stu-id="59068-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="59068-103">Identifie la source d'un objet pour lequel l'espace occupé en mémoire peut être récupéré.</span><span class="sxs-lookup"><span data-stu-id="59068-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59068-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59068-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="59068-105">Membres</span><span class="sxs-lookup"><span data-stu-id="59068-105">Members</span></span>  
  
|<span data-ttu-id="59068-106">Nom de membre</span><span class="sxs-lookup"><span data-stu-id="59068-106">Member name</span></span>|<span data-ttu-id="59068-107">Description</span><span class="sxs-lookup"><span data-stu-id="59068-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="59068-108">Handle à une référence forte tiré de la table de handles d'objets.</span><span class="sxs-lookup"><span data-stu-id="59068-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="59068-109">A handle to a pinned strong reference from the object handle table.</span><span class="sxs-lookup"><span data-stu-id="59068-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="59068-110">A handle to a weak reference from the object handle table.</span><span class="sxs-lookup"><span data-stu-id="59068-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="59068-111">A handle to a weak reference-counted object from the object handle table.</span><span class="sxs-lookup"><span data-stu-id="59068-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="59068-112">A handle to a reference-counted object from the object handle table.</span><span class="sxs-lookup"><span data-stu-id="59068-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="59068-113">A handle to a dependent object from the object handle table.</span><span class="sxs-lookup"><span data-stu-id="59068-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="59068-114">Objet épinglé asynchrone tiré de la table de handles d'objets.</span><span class="sxs-lookup"><span data-stu-id="59068-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="59068-115">Handle fort qui conserve une taille approximative de la fermeture collective de tous les objets et racines d’objets au moment du Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="59068-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="59068-116">A reference from the managed stack.</span><span class="sxs-lookup"><span data-stu-id="59068-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="59068-117">A reference from the finalizer queue.</span><span class="sxs-lookup"><span data-stu-id="59068-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="59068-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="59068-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="59068-119">Return only strong references from the handle table.</span><span class="sxs-lookup"><span data-stu-id="59068-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="59068-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span><span class="sxs-lookup"><span data-stu-id="59068-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="59068-121">Return only weak references from the handle table.</span><span class="sxs-lookup"><span data-stu-id="59068-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="59068-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span><span class="sxs-lookup"><span data-stu-id="59068-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="59068-123">Return all references from the handle table.</span><span class="sxs-lookup"><span data-stu-id="59068-123">Return all references from the handle table.</span></span> <span data-ttu-id="59068-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span><span class="sxs-lookup"><span data-stu-id="59068-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59068-125">Notes</span><span class="sxs-lookup"><span data-stu-id="59068-125">Remarks</span></span>  
 <span data-ttu-id="59068-126">The `CorGCReferenceType` enumeration is used as follows:</span><span class="sxs-lookup"><span data-stu-id="59068-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
- <span data-ttu-id="59068-127">As the value of the `type` field of the [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span><span class="sxs-lookup"><span data-stu-id="59068-127">As the value of the `type` field of the [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
- <span data-ttu-id="59068-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span><span class="sxs-lookup"><span data-stu-id="59068-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59068-129">spécifications</span><span class="sxs-lookup"><span data-stu-id="59068-129">Requirements</span></span>  
 <span data-ttu-id="59068-130">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59068-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59068-131">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59068-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59068-132">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59068-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59068-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59068-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59068-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59068-134">See also</span></span>

- [<span data-ttu-id="59068-135">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="59068-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
