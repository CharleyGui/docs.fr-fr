---
title: ICorDebugInternalFrame2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2377773b471b387376f0284522ebe29d6b003ae3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910108"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="ee2a9-102">ICorDebugInternalFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="ee2a9-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="ee2a9-103">Fournit des informations sur les frames internes, y compris l’adresse et la position de la pile par rapport aux objets ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="ee2a9-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee2a9-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ee2a9-104">Methods</span></span>  
  
|<span data-ttu-id="ee2a9-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ee2a9-105">Method</span></span>|<span data-ttu-id="ee2a9-106">Description</span><span class="sxs-lookup"><span data-stu-id="ee2a9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee2a9-107">GetFrameAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="ee2a9-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="ee2a9-108">Retourne l’adresse de la pile du frame interne.</span><span class="sxs-lookup"><span data-stu-id="ee2a9-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="ee2a9-109">IsCloserToLeaf, méthode</span><span class="sxs-lookup"><span data-stu-id="ee2a9-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="ee2a9-110">Vérifie si le `this` Frame interne est plus proche de la feuille que l’objet ICorDebugFrame spécifié.</span><span class="sxs-lookup"><span data-stu-id="ee2a9-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee2a9-111">Notes</span><span class="sxs-lookup"><span data-stu-id="ee2a9-111">Remarks</span></span>  
 <span data-ttu-id="ee2a9-112">Cette interface étend l’interface ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="ee2a9-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee2a9-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="ee2a9-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee2a9-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ee2a9-114">Requirements</span></span>  
 <span data-ttu-id="ee2a9-115">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee2a9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee2a9-116">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ee2a9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee2a9-117">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee2a9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee2a9-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee2a9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2a9-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee2a9-119">See also</span></span>

- [<span data-ttu-id="ee2a9-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ee2a9-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ee2a9-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="ee2a9-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
