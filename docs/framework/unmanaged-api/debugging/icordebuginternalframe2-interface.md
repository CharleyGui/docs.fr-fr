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
ms.openlocfilehash: 5a451218e0fdc32132a4e79d091ada8355d32fe7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122687"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="a5175-102">ICorDebugInternalFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="a5175-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="a5175-103">Fournit des informations sur les frames internes, y compris l’adresse et la position de la pile par rapport aux objets ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="a5175-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5175-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a5175-104">Methods</span></span>  
  
|<span data-ttu-id="a5175-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="a5175-105">Method</span></span>|<span data-ttu-id="a5175-106">Description</span><span class="sxs-lookup"><span data-stu-id="a5175-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5175-107">GetFrameAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="a5175-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="a5175-108">Retourne l’adresse de la pile du frame interne.</span><span class="sxs-lookup"><span data-stu-id="a5175-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="a5175-109">IsCloserToLeaf, méthode</span><span class="sxs-lookup"><span data-stu-id="a5175-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="a5175-110">Vérifie si le `this` Frame interne est plus proche de la feuille que l’objet ICorDebugFrame spécifié.</span><span class="sxs-lookup"><span data-stu-id="a5175-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5175-111">Notes</span><span class="sxs-lookup"><span data-stu-id="a5175-111">Remarks</span></span>  
 <span data-ttu-id="a5175-112">Cette interface étend l’interface ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="a5175-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5175-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="a5175-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5175-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="a5175-114">Requirements</span></span>  
 <span data-ttu-id="a5175-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5175-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5175-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5175-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5175-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5175-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5175-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5175-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5175-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5175-119">See also</span></span>

- [<span data-ttu-id="a5175-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a5175-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a5175-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="a5175-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
