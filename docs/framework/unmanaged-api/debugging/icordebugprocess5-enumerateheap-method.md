---
title: ICorDebugProcess5::EnumerateHeap, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: 22ab29f8a204a4b27dafdefcd3652cc3dcf9769c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671133"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="30c6c-102">ICorDebugProcess5::EnumerateHeap, méthode</span><span class="sxs-lookup"><span data-stu-id="30c6c-102">ICorDebugProcess5::EnumerateHeap Method</span></span>

<span data-ttu-id="30c6c-103">Obtient un énumérateur pour les objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="30c6c-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30c6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30c6c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30c6c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="30c6c-105">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="30c6c-106">à Pointeur vers l’adresse d’un objet d’interface [icordebugheapenum,](icordebugheapenum-interface.md) qui est un énumérateur pour les objets qui résident sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="30c6c-106">[out] A pointer to the address of an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30c6c-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="30c6c-107">Remarks</span></span>  

 <span data-ttu-id="30c6c-108">Avant d’appeler la `ICorDebugProcess5::EnumerateHeap` méthode, vous devez appeler la méthode [ICorDebugProcess5 :: getgcheapinformation,](icordebugprocess5-getgcheapinformation-method.md) et examiner la valeur du `areGCStructuresValid` champ de l’objet [COR_HEAPINFO](cor-heapinfo-structure.md) retourné pour vous assurer que le segment de mémoire garbage collection dans son état actuel est énumérable.</span><span class="sxs-lookup"><span data-stu-id="30c6c-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="30c6c-109">De plus, `ICorDebugProcess5::EnumerateHeap` retourne `E_FAIL` si vous attachez trop tôt au cours de la durée de vie du processus, avant d’allouer de la mémoire pour le tas managé.</span><span class="sxs-lookup"><span data-stu-id="30c6c-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="30c6c-110">L’objet d’interface [icordebugheapenum,](icordebugheapenum-interface.md) est un énumérateur standard dérivé de l’interface ICorDebugEnum qui vous permet d’énumérer des objets [COR_HEAPOBJECT](cor-heapobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="30c6c-110">The [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="30c6c-111">Cette méthode remplit l’objet de collection [icordebugheapenum,](icordebugheapenum-interface.md) avec [COR_HEAPOBJECT](cor-heapobject-structure.md) instances qui fournissent des informations sur tous les objets.</span><span class="sxs-lookup"><span data-stu-id="30c6c-111">This method populates the [ICorDebugHeapEnum](icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="30c6c-112">La collection peut également inclure des instances [COR_HEAPOBJECT](cor-heapobject-structure.md) qui fournissent des informations sur les objets qui ne sont enracinés par aucun objet, mais qui n’ont pas encore été collectés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="30c6c-112">The collection may also include [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30c6c-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="30c6c-113">Requirements</span></span>  

 <span data-ttu-id="30c6c-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30c6c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30c6c-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30c6c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30c6c-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30c6c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30c6c-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30c6c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c6c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30c6c-118">See also</span></span>

- [<span data-ttu-id="30c6c-119">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="30c6c-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="30c6c-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="30c6c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
