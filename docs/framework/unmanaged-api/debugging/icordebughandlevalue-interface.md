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
ms.openlocfilehash: 94472e84b73cdffe09505088b1e7fbc20a209bc3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138480"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="ec88a-102">ICorDebugHandleValue, interface</span><span class="sxs-lookup"><span data-stu-id="ec88a-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="ec88a-103">Sous-classe de ICorDebugReferenceValue qui représente une valeur de référence dans laquelle le débogueur a créé un handle pour garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ec88a-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec88a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ec88a-104">Methods</span></span>  
  
|<span data-ttu-id="ec88a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ec88a-105">Method</span></span>|<span data-ttu-id="ec88a-106">Description</span><span class="sxs-lookup"><span data-stu-id="ec88a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec88a-107">Dispose, méthode</span><span class="sxs-lookup"><span data-stu-id="ec88a-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="ec88a-108">Libère le handle référencé par cet objet `ICorDebugHandleValue` sans libérer explicitement le pointeur d’interface.</span><span class="sxs-lookup"><span data-stu-id="ec88a-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="ec88a-109">GetHandleType, méthode</span><span class="sxs-lookup"><span data-stu-id="ec88a-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="ec88a-110">Obtient une valeur CorDebugHandleType, qui décrit le genre de handle référencé par cet `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="ec88a-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec88a-111">Notes</span><span class="sxs-lookup"><span data-stu-id="ec88a-111">Remarks</span></span>  
 <span data-ttu-id="ec88a-112">Un objet `ICorDebugReferenceValue` est invalidé par un arrêt dans l’exécution du code débogué.</span><span class="sxs-lookup"><span data-stu-id="ec88a-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="ec88a-113">Un `ICorDebugHandleValue` conserve sa référence par des arrêts et des continuations, jusqu’à ce qu’il soit explicitement libéré.</span><span class="sxs-lookup"><span data-stu-id="ec88a-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec88a-114">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="ec88a-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec88a-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="ec88a-115">Requirements</span></span>  
 <span data-ttu-id="ec88a-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec88a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec88a-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec88a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec88a-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec88a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec88a-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec88a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec88a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec88a-120">See also</span></span>

- [<span data-ttu-id="ec88a-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ec88a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
