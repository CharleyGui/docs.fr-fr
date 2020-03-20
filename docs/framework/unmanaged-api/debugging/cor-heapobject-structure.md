---
title: COR_HEAPOBJECT, structure
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: efb3d913e1d8ef0c486d7e5e1d9777ae7d88bc71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179336"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="c92bf-102">COR_HEAPOBJECT, structure</span><span class="sxs-lookup"><span data-stu-id="c92bf-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="c92bf-103">Fournit des informations à propos d’un objet sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="c92bf-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c92bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c92bf-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="c92bf-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c92bf-105">Members</span></span>  
  
|<span data-ttu-id="c92bf-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c92bf-106">Member</span></span>|<span data-ttu-id="c92bf-107">Description</span><span class="sxs-lookup"><span data-stu-id="c92bf-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="c92bf-108">L’adresse de l’objet en mémoire.</span><span class="sxs-lookup"><span data-stu-id="c92bf-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="c92bf-109">La taille totale de l’objet, dans les octets.</span><span class="sxs-lookup"><span data-stu-id="c92bf-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="c92bf-110">Un [COR_TYPEID](cor-typeid-structure.md) jeton qui représente le type de l’objet.</span><span class="sxs-lookup"><span data-stu-id="c92bf-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c92bf-111">Notes </span><span class="sxs-lookup"><span data-stu-id="c92bf-111">Remarks</span></span>  
 <span data-ttu-id="c92bf-112">`COR_HEAPOBJECT`les instances peuvent être récupérées en énumérant un objet d’interface [ICorDebugHeapEnum](icordebugheapenum-interface.md) qui est peuplé en appelant le [ICorDebugProcess5::Méthode D’énumérationheap.](icordebugprocess5-enumerateheap-method.md)</span><span class="sxs-lookup"><span data-stu-id="c92bf-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="c92bf-113">Une `COR_HEAPOBJECT` instance fournit des informations soit sur un objet en direct sur le tas géré, soit sur un objet qui n’est pas enraciné par un objet mais qui n’a pas encore été recueilli par le collecteur d’ordures.</span><span class="sxs-lookup"><span data-stu-id="c92bf-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="c92bf-114">Pour de meilleures `COR_HEAPOBJECT.address` performances, `CORDB_ADDRESS` le champ est une valeur plutôt que la valeur iCorDebugValue interface utilisée dans une grande partie de l’API débogage.</span><span class="sxs-lookup"><span data-stu-id="c92bf-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="c92bf-115">Pour obtenir un objet ICorDebugValue pour une adresse `CORDB_ADDRESS` d’objet donnée, vous pouvez transmettre la valeur à la méthode [ICorDebugProcess5::GetObject.](icordebugprocess5-getobject-method.md)</span><span class="sxs-lookup"><span data-stu-id="c92bf-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="c92bf-116">Pour de meilleures `COR_HEAPOBJECT.type` performances, `COR_TYPEID` le champ est une valeur plutôt que la valeur iCorDebugType interface utilisée dans une grande partie de l’API débogage.</span><span class="sxs-lookup"><span data-stu-id="c92bf-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="c92bf-117">Pour obtenir un objet ICorDebugType pour un ID `COR_TYPEID` de type donné, vous pouvez transmettre la valeur à la méthode [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) méthode.</span><span class="sxs-lookup"><span data-stu-id="c92bf-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="c92bf-118">La `COR_HEAPOBJECT` structure comprend une interface COM comptée de référence.</span><span class="sxs-lookup"><span data-stu-id="c92bf-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="c92bf-119">Si vous `COR_HEAPOBJECT` récupérez une instance de l’enumérateur en appelant [l’ICorDebugHeapEnum: :Méthode suivante,](icordebugheapenum-next-method.md) vous devez par la suite libérer la référence.</span><span class="sxs-lookup"><span data-stu-id="c92bf-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c92bf-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c92bf-120">Requirements</span></span>  
 <span data-ttu-id="c92bf-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c92bf-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c92bf-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c92bf-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c92bf-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c92bf-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c92bf-124">**.NET Versions-cadre:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c92bf-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c92bf-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c92bf-125">See also</span></span>

- [<span data-ttu-id="c92bf-126">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="c92bf-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="c92bf-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="c92bf-127">Debugging</span></span>](index.md)
