---
title: ICorDebugReferenceValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: 2efba22b4ec372c5ddedd4982a29d66945d3511c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792129"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="4d195-102">ICorDebugReferenceValue, interface</span><span class="sxs-lookup"><span data-stu-id="4d195-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="4d195-103">Fournit des méthodes qui gèrent une valeur qui est une référence à un objet.</span><span class="sxs-lookup"><span data-stu-id="4d195-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="4d195-104">(Autrement dit, cette interface fournit des méthodes qui gèrent un pointeur.) Cette interface implémente « ICorDebugValue ».</span><span class="sxs-lookup"><span data-stu-id="4d195-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d195-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4d195-105">Methods</span></span>  
  
|<span data-ttu-id="4d195-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="4d195-106">Method</span></span>|<span data-ttu-id="4d195-107">Description</span><span class="sxs-lookup"><span data-stu-id="4d195-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d195-108">Dereference, méthode</span><span class="sxs-lookup"><span data-stu-id="4d195-108">Dereference Method</span></span>](icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="4d195-109">Obtient l’objet référencé.</span><span class="sxs-lookup"><span data-stu-id="4d195-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="4d195-110">DereferenceStrong, méthode</span><span class="sxs-lookup"><span data-stu-id="4d195-110">DereferenceStrong Method</span></span>](icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="4d195-111">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="4d195-111">Not implemented.</span></span> <span data-ttu-id="4d195-112">N'appelez pas cette méthode.</span><span class="sxs-lookup"><span data-stu-id="4d195-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="4d195-113">GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="4d195-113">GetValue Method</span></span>](icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="4d195-114">Obtient l’adresse mémoire actuelle de l’objet référencé.</span><span class="sxs-lookup"><span data-stu-id="4d195-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="4d195-115">IsNull, méthode</span><span class="sxs-lookup"><span data-stu-id="4d195-115">IsNull Method</span></span>](icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="4d195-116">Obtient une valeur qui indique si ce `ICorDebugReferenceValue` est une valeur null, auquel cas le `ICorDebugReferenceValue` ne pointe pas vers un objet.</span><span class="sxs-lookup"><span data-stu-id="4d195-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="4d195-117">SetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="4d195-117">SetValue Method</span></span>](icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="4d195-118">Définit l’adresse mémoire actuelle.</span><span class="sxs-lookup"><span data-stu-id="4d195-118">Sets the current memory address.</span></span> <span data-ttu-id="4d195-119">Autrement dit, cette méthode définit ce `ICorDebugReferenceValue` pour pointer vers un objet.</span><span class="sxs-lookup"><span data-stu-id="4d195-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d195-120">Notes</span><span class="sxs-lookup"><span data-stu-id="4d195-120">Remarks</span></span>  
 <span data-ttu-id="4d195-121">Le common language runtime (CLR) peut effectuer une garbage collection sur les objets lorsque le processus débogué est poursuivi.</span><span class="sxs-lookup"><span data-stu-id="4d195-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="4d195-122">La garbage collection peut déplacer des objets dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="4d195-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="4d195-123">Une `ICorDebugReferenceValue` coopérera avec le garbage collection afin que ses informations soient mises à jour après le garbage collection ou qu’elles soient invalidées implicitement avant la garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4d195-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="4d195-124">L’objet `ICorDebugReferenceValue` peut être invalidé implicitement une fois que le processus débogué a été poursuivi.</span><span class="sxs-lookup"><span data-stu-id="4d195-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="4d195-125">Le « ICorDebugHandleValue » dérivé n’est pas invalidé tant qu’il n’a pas été explicitement libéré ou exposé.</span><span class="sxs-lookup"><span data-stu-id="4d195-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d195-126">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="4d195-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d195-127">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="4d195-127">Requirements</span></span>  
 <span data-ttu-id="4d195-128">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d195-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d195-129">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d195-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d195-130">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d195-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d195-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d195-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d195-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d195-132">See also</span></span>

- [<span data-ttu-id="4d195-133">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4d195-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
