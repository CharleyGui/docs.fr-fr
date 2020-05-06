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
ms.openlocfilehash: d156f103c3812c91da380e722a1c6c95d621df4c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860920"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="8475d-102">CorGCReferenceType, énumération</span><span class="sxs-lookup"><span data-stu-id="8475d-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="8475d-103">Identifie la source d'un objet pour lequel l'espace occupé en mémoire peut être récupéré.</span><span class="sxs-lookup"><span data-stu-id="8475d-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8475d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8475d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8475d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="8475d-105">Members</span></span>  
  
|<span data-ttu-id="8475d-106">Nom de membre</span><span class="sxs-lookup"><span data-stu-id="8475d-106">Member name</span></span>|<span data-ttu-id="8475d-107">Description</span><span class="sxs-lookup"><span data-stu-id="8475d-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="8475d-108">Handle à une référence forte tiré de la table de handles d'objets.</span><span class="sxs-lookup"><span data-stu-id="8475d-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="8475d-109">Handle d’une référence forte épinglée de la table de handles d’objets.</span><span class="sxs-lookup"><span data-stu-id="8475d-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="8475d-110">Handle d’une référence faible à partir de la table de handles d’objets.</span><span class="sxs-lookup"><span data-stu-id="8475d-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="8475d-111">Handle d’un objet de référence faible à partir de la table de handles d’objets.</span><span class="sxs-lookup"><span data-stu-id="8475d-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="8475d-112">Handle d’un objet compté en référence à partir de la table de handles d’objets.</span><span class="sxs-lookup"><span data-stu-id="8475d-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="8475d-113">Handle vers un objet dépendant de la table de handles d’objets.</span><span class="sxs-lookup"><span data-stu-id="8475d-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="8475d-114">Objet épinglé asynchrone tiré de la table de handles d'objets.</span><span class="sxs-lookup"><span data-stu-id="8475d-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="8475d-115">Handle fort qui conserve une taille approximative de la fermeture collective de tous les objets et racines d’objets au moment du Garbage Collection.</span><span class="sxs-lookup"><span data-stu-id="8475d-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="8475d-116">Référence à partir de la pile managée.</span><span class="sxs-lookup"><span data-stu-id="8475d-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="8475d-117">Référence à partir de la file d’attente du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="8475d-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="8475d-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="8475d-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="8475d-119">Retourne uniquement les références fortes de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="8475d-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="8475d-120">Cette valeur est utilisée uniquement par la méthode [ICorDebugProcess5 :: enumeratehandles,](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8475d-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="8475d-121">Retourne uniquement les références faibles de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="8475d-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="8475d-122">Cette valeur est utilisée uniquement par la méthode [ICorDebugProcess5 :: enumeratehandles,](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8475d-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="8475d-123">Retourne toutes les références de la table de handles.</span><span class="sxs-lookup"><span data-stu-id="8475d-123">Return all references from the handle table.</span></span> <span data-ttu-id="8475d-124">Cette valeur est utilisée uniquement par la méthode [ICorDebugProcess5 :: enumeratehandles,](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8475d-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8475d-125">Notes </span><span class="sxs-lookup"><span data-stu-id="8475d-125">Remarks</span></span>  
 <span data-ttu-id="8475d-126">L' `CorGCReferenceType` énumération est utilisée comme suit :</span><span class="sxs-lookup"><span data-stu-id="8475d-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
- <span data-ttu-id="8475d-127">En tant que valeur du `type` champ de la structure [COR_GC_REFERENCE](cor-gc-reference-structure.md) , elle indique la source d’une référence ou d’un handle.</span><span class="sxs-lookup"><span data-stu-id="8475d-127">As the value of the `type` field of the [COR_GC_REFERENCE](cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
- <span data-ttu-id="8475d-128">En tant `types` qu’argument de la méthode [ICorDebugProcess5 :: enumeratehandles,](icordebugprocess5-enumeratehandles-method.md) , il spécifie les types de handles à inclure dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="8475d-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8475d-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8475d-129">Requirements</span></span>  
 <span data-ttu-id="8475d-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8475d-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8475d-131">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8475d-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8475d-132">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8475d-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8475d-133">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8475d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8475d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8475d-134">See also</span></span>

- [<span data-ttu-id="8475d-135">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="8475d-135">Debugging Enumerations</span></span>](debugging-enumerations.md)
