---
title: ICorDebugObjectValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: b782207503a2c3f739a30f68d509e6b481d2b6a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129754"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="b9a8b-102">ICorDebugObjectValue, interface</span><span class="sxs-lookup"><span data-stu-id="b9a8b-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="b9a8b-103">Sous-classe de « ICorDebugValue » qui représente une valeur qui contient un objet.</span><span class="sxs-lookup"><span data-stu-id="b9a8b-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9a8b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b9a8b-104">Methods</span></span>  
  
|<span data-ttu-id="b9a8b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b9a8b-105">Method</span></span>|<span data-ttu-id="b9a8b-106">Description</span><span class="sxs-lookup"><span data-stu-id="b9a8b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9a8b-107">GetClass, méthode</span><span class="sxs-lookup"><span data-stu-id="b9a8b-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="b9a8b-108">Obtient un pointeur d’interface vers le common language runtime (CLR) <xref:System.Type> de l’objet référencé par ce `ICorDebugObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="b9a8b-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="b9a8b-109">GetContext, méthode</span><span class="sxs-lookup"><span data-stu-id="b9a8b-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="b9a8b-110">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="b9a8b-110">Not implemented.</span></span>|  
|[<span data-ttu-id="b9a8b-111">GetFieldValue, méthode</span><span class="sxs-lookup"><span data-stu-id="b9a8b-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="b9a8b-112">Obtient un pointeur d’interface vers un [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) qui représente la valeur du champ spécifié de la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b9a8b-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="b9a8b-113">GetManagedCopy, méthode</span><span class="sxs-lookup"><span data-stu-id="b9a8b-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="b9a8b-114">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b9a8b-114">Obsolete.</span></span> <span data-ttu-id="b9a8b-115">N'appelez pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="b9a8b-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="b9a8b-116">GetVirtualMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="b9a8b-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="b9a8b-117">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="b9a8b-117">Not implemented.</span></span>|  
|[<span data-ttu-id="b9a8b-118">IsValueClass, méthode</span><span class="sxs-lookup"><span data-stu-id="b9a8b-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="b9a8b-119">Obtient une valeur qui indique si l’objet référencé par ce `ICorDebugObjectValue` est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="b9a8b-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="b9a8b-120">SetFromManagedCopy, méthode</span><span class="sxs-lookup"><span data-stu-id="b9a8b-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="b9a8b-121">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="b9a8b-121">Obsolete.</span></span> <span data-ttu-id="b9a8b-122">N'appelez pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="b9a8b-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9a8b-123">Notes</span><span class="sxs-lookup"><span data-stu-id="b9a8b-123">Remarks</span></span>  
 <span data-ttu-id="b9a8b-124">Une `ICorDebugObjectValue` reste valide jusqu’à ce que le processus en cours de débogage se poursuive.</span><span class="sxs-lookup"><span data-stu-id="b9a8b-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9a8b-125">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="b9a8b-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9a8b-126">spécifications</span><span class="sxs-lookup"><span data-stu-id="b9a8b-126">Requirements</span></span>  
 <span data-ttu-id="b9a8b-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9a8b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9a8b-128">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9a8b-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9a8b-129">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9a8b-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9a8b-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9a8b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a8b-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9a8b-131">See also</span></span>

- [<span data-ttu-id="b9a8b-132">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b9a8b-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
