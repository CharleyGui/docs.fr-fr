---
title: ICorDebugBlockingObjectEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11693416d0a3e0afe80c2356ff0a12ecea0d8d15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959309"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="30da6-102">ICorDebugBlockingObjectEnum, interface</span><span class="sxs-lookup"><span data-stu-id="30da6-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="30da6-103">Fournit un énumérateur pour une liste de structures [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="30da6-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="30da6-104">Cette interface est une sous-classe de l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="30da6-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="30da6-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="30da6-105">Methods</span></span>  
  
|<span data-ttu-id="30da6-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="30da6-106">Method</span></span>|<span data-ttu-id="30da6-107">Description</span><span class="sxs-lookup"><span data-stu-id="30da6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="30da6-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="30da6-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="30da6-109">Énumère une liste de structures [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="30da6-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30da6-110">Notes</span><span class="sxs-lookup"><span data-stu-id="30da6-110">Remarks</span></span>  
 <span data-ttu-id="30da6-111">Chaque structure `CorDebugBlockingObject` représente un objet qui bloque un thread.</span><span class="sxs-lookup"><span data-stu-id="30da6-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30da6-112">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="30da6-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30da6-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="30da6-113">Requirements</span></span>  
 <span data-ttu-id="30da6-114">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30da6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30da6-115">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="30da6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30da6-116">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30da6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30da6-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30da6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30da6-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30da6-118">See also</span></span>

- [<span data-ttu-id="30da6-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="30da6-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="30da6-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="30da6-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
