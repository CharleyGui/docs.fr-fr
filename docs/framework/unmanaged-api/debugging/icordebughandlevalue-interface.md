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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3219554cf953b8de31e236b2f484478172673f7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915010"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="242fe-102">ICorDebugHandleValue, interface</span><span class="sxs-lookup"><span data-stu-id="242fe-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="242fe-103">Sous-classe de ICorDebugReferenceValue qui représente une valeur de référence dans laquelle le débogueur a créé un handle pour garbage collection.</span><span class="sxs-lookup"><span data-stu-id="242fe-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="242fe-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="242fe-104">Methods</span></span>  
  
|<span data-ttu-id="242fe-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="242fe-105">Method</span></span>|<span data-ttu-id="242fe-106">Description</span><span class="sxs-lookup"><span data-stu-id="242fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="242fe-107">Dispose, méthode</span><span class="sxs-lookup"><span data-stu-id="242fe-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="242fe-108">Libère le handle référencé par cet `ICorDebugHandleValue` objet sans libérer explicitement le pointeur d’interface.</span><span class="sxs-lookup"><span data-stu-id="242fe-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="242fe-109">GetHandleType, méthode</span><span class="sxs-lookup"><span data-stu-id="242fe-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="242fe-110">Obtient une valeur CorDebugHandleType, qui décrit le genre de handle référencé par ce `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="242fe-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="242fe-111">Notes</span><span class="sxs-lookup"><span data-stu-id="242fe-111">Remarks</span></span>  
 <span data-ttu-id="242fe-112">Un `ICorDebugReferenceValue` objet est invalidé par un arrêt dans l’exécution du code débogué.</span><span class="sxs-lookup"><span data-stu-id="242fe-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="242fe-113">Un `ICorDebugHandleValue` maintient sa référence via des arrêts et des continuations, jusqu’à ce qu’il soit explicitement libéré.</span><span class="sxs-lookup"><span data-stu-id="242fe-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="242fe-114">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="242fe-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="242fe-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="242fe-115">Requirements</span></span>  
 <span data-ttu-id="242fe-116">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="242fe-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="242fe-117">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="242fe-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="242fe-118">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="242fe-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="242fe-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="242fe-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="242fe-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="242fe-120">See also</span></span>

- [<span data-ttu-id="242fe-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="242fe-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
