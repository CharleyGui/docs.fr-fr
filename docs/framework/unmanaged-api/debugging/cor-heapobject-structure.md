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
ms.openlocfilehash: 54af02b48dabdf2042763954805f0d454323ac89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726364"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="dbe58-102">COR_HEAPOBJECT, structure</span><span class="sxs-lookup"><span data-stu-id="dbe58-102">COR_HEAPOBJECT Structure</span></span>

<span data-ttu-id="dbe58-103">Fournit des informations à propos d’un objet sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="dbe58-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbe58-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="dbe58-105">Membres</span><span class="sxs-lookup"><span data-stu-id="dbe58-105">Members</span></span>  
  
|<span data-ttu-id="dbe58-106">Membre</span><span class="sxs-lookup"><span data-stu-id="dbe58-106">Member</span></span>|<span data-ttu-id="dbe58-107">Description</span><span class="sxs-lookup"><span data-stu-id="dbe58-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="dbe58-108">Adresse de l’objet en mémoire.</span><span class="sxs-lookup"><span data-stu-id="dbe58-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="dbe58-109">Taille totale de l’objet, en octets.</span><span class="sxs-lookup"><span data-stu-id="dbe58-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="dbe58-110">Jeton [COR_TYPEID](cor-typeid-structure.md) qui représente le type de l’objet.</span><span class="sxs-lookup"><span data-stu-id="dbe58-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbe58-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="dbe58-111">Remarks</span></span>  

 <span data-ttu-id="dbe58-112">`COR_HEAPOBJECT` les instances peuvent être récupérées en énumérant un objet d’interface [icordebugheapenum,](icordebugheapenum-interface.md) rempli par l’appel de la méthode [ICorDebugProcess5 :: enumerateheap,](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dbe58-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="dbe58-113">Une `COR_HEAPOBJECT` instance de fournit des informations sur un objet actif sur le tas managé, ou sur un objet qui n’est associé à aucun objet, mais qui n’a pas encore été collecté par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="dbe58-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="dbe58-114">Pour de meilleures performances, le `COR_HEAPOBJECT.address` champ est une `CORDB_ADDRESS` valeur plutôt que la valeur d’interface ICorDebugValue utilisée dans la plupart de l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="dbe58-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="dbe58-115">Pour obtenir un objet ICorDebugValue pour une adresse d’objet donnée, vous pouvez passer la `CORDB_ADDRESS` valeur à la méthode [ICorDebugProcess5 :: GetObject](icordebugprocess5-getobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dbe58-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="dbe58-116">Pour de meilleures performances, le `COR_HEAPOBJECT.type` champ est une `COR_TYPEID` valeur plutôt que la valeur d’interface ICorDebugType utilisée dans la plupart de l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="dbe58-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="dbe58-117">Pour obtenir un objet ICorDebugType pour un ID de type donné, vous pouvez passer la `COR_TYPEID` valeur à la méthode [ICorDebugProcess5 :: gettypefortypeid,](icordebugprocess5-gettypefortypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dbe58-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="dbe58-118">La `COR_HEAPOBJECT` structure comprend une interface com avec comptage des références.</span><span class="sxs-lookup"><span data-stu-id="dbe58-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="dbe58-119">Si vous récupérez une `COR_HEAPOBJECT` instance de l’énumérateur en appelant la méthode [icordebugheapenum, :: Next](icordebugheapenum-next-method.md) , vous devez libérer ultérieurement la référence.</span><span class="sxs-lookup"><span data-stu-id="dbe58-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbe58-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dbe58-120">Requirements</span></span>  

 <span data-ttu-id="dbe58-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbe58-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbe58-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbe58-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbe58-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbe58-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbe58-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbe58-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe58-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbe58-125">See also</span></span>

- [<span data-ttu-id="dbe58-126">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="dbe58-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="dbe58-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="dbe58-127">Debugging</span></span>](index.md)
