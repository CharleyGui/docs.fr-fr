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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cbecd5be9b1ac7c08e6970933a48eeb95f01a22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739381"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="814dc-102">CorGCReferenceType, énumération</span><span class="sxs-lookup"><span data-stu-id="814dc-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="814dc-103">Identifie la source d'un objet pour lequel l'espace occupé en mémoire peut être récupéré.</span><span class="sxs-lookup"><span data-stu-id="814dc-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="814dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="814dc-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="814dc-105">Membres</span><span class="sxs-lookup"><span data-stu-id="814dc-105">Members</span></span>  
  
|<span data-ttu-id="814dc-106">Nom de membre</span><span class="sxs-lookup"><span data-stu-id="814dc-106">Member name</span></span>|<span data-ttu-id="814dc-107">Description</span><span class="sxs-lookup"><span data-stu-id="814dc-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="814dc-108">Handle à une référence forte tiré de la table de handles d'objets.</span><span class="sxs-lookup"><span data-stu-id="814dc-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="814dc-109">Handle vers une référence forte épinglée à partir de la table de handles d’objet.</span><span class="sxs-lookup"><span data-stu-id="814dc-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="814dc-110">Handle vers une référence faible à partir de la table de handles d’objet.</span><span class="sxs-lookup"><span data-stu-id="814dc-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="814dc-111">Handle vers un objet contenant des références faible à partir de la table de handles d’objet.</span><span class="sxs-lookup"><span data-stu-id="814dc-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="814dc-112">Handle vers un objet contenant des références à partir de la table de handles d’objet.</span><span class="sxs-lookup"><span data-stu-id="814dc-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="814dc-113">Handle vers un objet dépendant à partir de la table de handles d’objet.</span><span class="sxs-lookup"><span data-stu-id="814dc-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="814dc-114">Objet épinglé asynchrone tiré de la table de handles d'objets.</span><span class="sxs-lookup"><span data-stu-id="814dc-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="814dc-115">Handle fort qui conserve une taille approximative de la fermeture collective de tous les objets et racines d’objets au moment du Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="814dc-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="814dc-116">Une référence à partir de la pile gérée.</span><span class="sxs-lookup"><span data-stu-id="814dc-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="814dc-117">Une référence à partir de la file d’attente du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="814dc-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="814dc-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="814dc-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="814dc-119">Retourner uniquement les références fortes à partir de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="814dc-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="814dc-120">Cette valeur est utilisée par le [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) méthode uniquement.</span><span class="sxs-lookup"><span data-stu-id="814dc-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="814dc-121">Retourner uniquement les références faibles à partir de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="814dc-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="814dc-122">Cette valeur est utilisée par le [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) méthode uniquement.</span><span class="sxs-lookup"><span data-stu-id="814dc-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="814dc-123">Retourner toutes les références à partir de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="814dc-123">Return all references from the handle table.</span></span> <span data-ttu-id="814dc-124">Cette valeur est utilisée par le [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) méthode uniquement.</span><span class="sxs-lookup"><span data-stu-id="814dc-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="814dc-125">Notes</span><span class="sxs-lookup"><span data-stu-id="814dc-125">Remarks</span></span>  
 <span data-ttu-id="814dc-126">Le `CorGCReferenceType` énumération est utilisée comme suit :</span><span class="sxs-lookup"><span data-stu-id="814dc-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
- <span data-ttu-id="814dc-127">En tant que la valeur de la `type` champ la [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, il indique la source d’une référence ou un handle.</span><span class="sxs-lookup"><span data-stu-id="814dc-127">As the value of the `type` field of the [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
- <span data-ttu-id="814dc-128">Comme le `types` l’argument de la [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) méthode, il spécifie les types de handles à inclure dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="814dc-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="814dc-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="814dc-129">Requirements</span></span>  
 <span data-ttu-id="814dc-130">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="814dc-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="814dc-131">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="814dc-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="814dc-132">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="814dc-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="814dc-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="814dc-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="814dc-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="814dc-134">See also</span></span>

- [<span data-ttu-id="814dc-135">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="814dc-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
