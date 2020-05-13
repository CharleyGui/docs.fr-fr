---
title: ICorDebugProcess5, interface
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
ms.openlocfilehash: 1953a3e0492e4cfcdaea761b68ea22cf5a4a8ed7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205516"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="9526c-102">ICorDebugProcess5, interface</span><span class="sxs-lookup"><span data-stu-id="9526c-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="9526c-103">Étend l’interface ICorDebugProcess pour prendre en charge l’accès au tas managé, pour fournir des informations sur garbage collection d’objets managés et pour déterminer si un débogueur charge des images à partir du cache des images natives locales de l’application.</span><span class="sxs-lookup"><span data-stu-id="9526c-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9526c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9526c-104">Methods</span></span>  
  
|<span data-ttu-id="9526c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9526c-105">Method</span></span>|<span data-ttu-id="9526c-106">Description</span><span class="sxs-lookup"><span data-stu-id="9526c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9526c-107">EnableNGenPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="9526c-107">EnableNGenPolicy Method</span></span>](icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="9526c-108">Définit une valeur qui détermine la façon dont une application charge les images natives lors de l’exécution sous un débogueur managé.</span><span class="sxs-lookup"><span data-stu-id="9526c-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="9526c-109">EnumerateGCReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="9526c-109">EnumerateGCReferences Method</span></span>](icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="9526c-110">Obtient un énumérateur pour tous les objets qui doivent être récupérés par le garbage collector dans un processus.</span><span class="sxs-lookup"><span data-stu-id="9526c-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="9526c-111">EnumerateHandles, méthode</span><span class="sxs-lookup"><span data-stu-id="9526c-111">EnumerateHandles Method</span></span>](icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="9526c-112">Obtient un énumérateur pour les handles d’objet dans un processus.</span><span class="sxs-lookup"><span data-stu-id="9526c-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="9526c-113">EnumerateHeap, méthode</span><span class="sxs-lookup"><span data-stu-id="9526c-113">EnumerateHeap Method</span></span>](icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="9526c-114">Obtient un énumérateur pour les objets sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="9526c-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="9526c-115">EnumerateHeapRegions, méthode</span><span class="sxs-lookup"><span data-stu-id="9526c-115">EnumerateHeapRegions Method</span></span>](icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="9526c-116">Obtient un énumérateur pour les régions du tas managé.</span><span class="sxs-lookup"><span data-stu-id="9526c-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="9526c-117">GetArrayLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="9526c-117">GetArrayLayout Method</span></span>](icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="9526c-118">Obtient des informations sur la disposition d’un tableau en mémoire.</span><span class="sxs-lookup"><span data-stu-id="9526c-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="9526c-119">GetGCHeapInformation, méthode</span><span class="sxs-lookup"><span data-stu-id="9526c-119">GetGCHeapInformation Method</span></span>](icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="9526c-120">Obtient un pointeur vers une structure [COR_HEAPINFO](cor-heapinfo-structure.md) qui contient des informations sur les objets qui doivent être récupérés par le garbage collector sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="9526c-120">Gets a pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="9526c-121">GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="9526c-121">GetObject Method</span></span>](icordebugprocess5-getobject-method.md)|<span data-ttu-id="9526c-122">Obtient un pointeur vers un objet sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="9526c-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="9526c-123">GetTypeFields, méthode</span><span class="sxs-lookup"><span data-stu-id="9526c-123">GetTypeFields Method</span></span>](icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="9526c-124">Obtient un pointeur vers un tableau qui contient des informations de champ pour un type en fonction de son identificateur de type.</span><span class="sxs-lookup"><span data-stu-id="9526c-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="9526c-125">GetTypeForTypeID, méthode</span><span class="sxs-lookup"><span data-stu-id="9526c-125">GetTypeForTypeID Method</span></span>](icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="9526c-126">Obtient un objet de type qui fournit des informations à propos d’un objet en fonction de ses identificateurs de type.</span><span class="sxs-lookup"><span data-stu-id="9526c-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="9526c-127">GetTypeID, méthode</span><span class="sxs-lookup"><span data-stu-id="9526c-127">GetTypeID Method</span></span>](icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="9526c-128">Obtient l’identificateur de type pour l’objet à une adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9526c-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="9526c-129">GetTypeLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="9526c-129">GetTypeLayout Method</span></span>](icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="9526c-130">Obtient des informations sur la disposition d’un objet en mémoire en fonction de son identificateur de type.</span><span class="sxs-lookup"><span data-stu-id="9526c-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9526c-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="9526c-131">Remarks</span></span>  
 <span data-ttu-id="9526c-132">Cette interface étend logiquement les interfaces ICorDebugProcess, ICorDebugProcess2 et [ICorDebugProcess3](icordebugprocess3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9526c-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9526c-133">Cette interface ne prend pas en charge l’appel à distance, à partir d’un autre ordinateur ou d’un autre processus.</span><span class="sxs-lookup"><span data-stu-id="9526c-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9526c-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9526c-134">Requirements</span></span>  
 <span data-ttu-id="9526c-135">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9526c-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9526c-136">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9526c-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9526c-137">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9526c-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9526c-138">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9526c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9526c-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9526c-139">See also</span></span>

- [<span data-ttu-id="9526c-140">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9526c-140">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9526c-141">Débogage</span><span class="sxs-lookup"><span data-stu-id="9526c-141">Debugging</span></span>](index.md)
