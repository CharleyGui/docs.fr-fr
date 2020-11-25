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
ms.openlocfilehash: 2a5a618491bf2c624669728d97a690cca315bff8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724674"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="2a2f4-102">ICorDebugObjectValue, interface</span><span class="sxs-lookup"><span data-stu-id="2a2f4-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="2a2f4-103">Sous-classe de « ICorDebugValue » qui représente une valeur qui contient un objet.</span><span class="sxs-lookup"><span data-stu-id="2a2f4-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a2f4-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2a2f4-104">Methods</span></span>  
  
|<span data-ttu-id="2a2f4-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="2a2f4-105">Method</span></span>|<span data-ttu-id="2a2f4-106">Description</span><span class="sxs-lookup"><span data-stu-id="2a2f4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a2f4-107">GetClass, méthode</span><span class="sxs-lookup"><span data-stu-id="2a2f4-107">GetClass Method</span></span>](icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="2a2f4-108">Obtient un pointeur d’interface vers le common language runtime (CLR) <xref:System.Type> de l’objet référencé par ce `ICorDebugObjectValue` .</span><span class="sxs-lookup"><span data-stu-id="2a2f4-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="2a2f4-109">GetContext, méthode</span><span class="sxs-lookup"><span data-stu-id="2a2f4-109">GetContext Method</span></span>](icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="2a2f4-110">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="2a2f4-110">Not implemented.</span></span>|  
|[<span data-ttu-id="2a2f4-111">GetFieldValue, méthode</span><span class="sxs-lookup"><span data-stu-id="2a2f4-111">GetFieldValue Method</span></span>](icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="2a2f4-112">Obtient un pointeur d’interface vers un [ICorDebugValue](icordebugvalue-interface.md) qui représente la valeur du champ spécifié de la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2a2f4-112">Gets an interface pointer to an [ICorDebugValue](icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="2a2f4-113">GetManagedCopy, méthode</span><span class="sxs-lookup"><span data-stu-id="2a2f4-113">GetManagedCopy Method</span></span>](icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="2a2f4-114">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="2a2f4-114">Obsolete.</span></span> <span data-ttu-id="2a2f4-115">N'appelez pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="2a2f4-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="2a2f4-116">GetVirtualMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="2a2f4-116">GetVirtualMethod Method</span></span>](icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="2a2f4-117">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="2a2f4-117">Not implemented.</span></span>|  
|[<span data-ttu-id="2a2f4-118">IsValueClass, méthode</span><span class="sxs-lookup"><span data-stu-id="2a2f4-118">IsValueClass Method</span></span>](icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="2a2f4-119">Obtient une valeur qui indique si l’objet référencé par ce `ICorDebugObjectValue` est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="2a2f4-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="2a2f4-120">SetFromManagedCopy, méthode</span><span class="sxs-lookup"><span data-stu-id="2a2f4-120">SetFromManagedCopy Method</span></span>](icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="2a2f4-121">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="2a2f4-121">Obsolete.</span></span> <span data-ttu-id="2a2f4-122">N'appelez pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="2a2f4-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a2f4-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="2a2f4-123">Remarks</span></span>  

 <span data-ttu-id="2a2f4-124">Un `ICorDebugObjectValue` reste valide jusqu’à ce que le processus en cours de débogage se poursuive.</span><span class="sxs-lookup"><span data-stu-id="2a2f4-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a2f4-125">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="2a2f4-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a2f4-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2a2f4-126">Requirements</span></span>  

 <span data-ttu-id="2a2f4-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a2f4-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a2f4-128">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a2f4-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a2f4-129">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a2f4-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a2f4-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a2f4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a2f4-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a2f4-131">See also</span></span>

- [<span data-ttu-id="2a2f4-132">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2a2f4-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
