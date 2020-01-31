---
title: ICorDebugHandleValue, interface
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: 406468fc6e2b68e8c8e1dfbd0f0f18cce3f013ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794455"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="19aa4-102">ICorDebugHandleValue, interface</span><span class="sxs-lookup"><span data-stu-id="19aa4-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="19aa4-103">Sous-classe de ICorDebugReferenceValue qui représente une valeur de référence dans laquelle le débogueur a créé un handle pour garbage collection.</span><span class="sxs-lookup"><span data-stu-id="19aa4-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19aa4-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="19aa4-104">Methods</span></span>  
  
|<span data-ttu-id="19aa4-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="19aa4-105">Method</span></span>|<span data-ttu-id="19aa4-106">Description</span><span class="sxs-lookup"><span data-stu-id="19aa4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19aa4-107">Dispose, méthode</span><span class="sxs-lookup"><span data-stu-id="19aa4-107">Dispose Method</span></span>](icordebughandlevalue-dispose-method.md)|<span data-ttu-id="19aa4-108">Libère le handle référencé par cet objet `ICorDebugHandleValue` sans libérer explicitement le pointeur d’interface.</span><span class="sxs-lookup"><span data-stu-id="19aa4-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="19aa4-109">GetHandleType, méthode</span><span class="sxs-lookup"><span data-stu-id="19aa4-109">GetHandleType Method</span></span>](icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="19aa4-110">Obtient une valeur CorDebugHandleType, qui décrit le genre de handle référencé par cet `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="19aa4-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19aa4-111">Notes</span><span class="sxs-lookup"><span data-stu-id="19aa4-111">Remarks</span></span>  
 <span data-ttu-id="19aa4-112">Un objet `ICorDebugReferenceValue` est invalidé par un arrêt dans l’exécution du code débogué.</span><span class="sxs-lookup"><span data-stu-id="19aa4-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="19aa4-113">Un `ICorDebugHandleValue` conserve sa référence par des arrêts et des continuations, jusqu’à ce qu’il soit explicitement libéré.</span><span class="sxs-lookup"><span data-stu-id="19aa4-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19aa4-114">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="19aa4-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19aa4-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="19aa4-115">Requirements</span></span>  
 <span data-ttu-id="19aa4-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19aa4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19aa4-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19aa4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19aa4-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19aa4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19aa4-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19aa4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19aa4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19aa4-120">See also</span></span>

- [<span data-ttu-id="19aa4-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="19aa4-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
