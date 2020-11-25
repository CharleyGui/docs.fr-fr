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
ms.openlocfilehash: a17c46d5ef08963bb0d7fc280ba8b90531e41c5b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719630"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="9ed30-102">ICorDebugInternalFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="9ed30-102">ICorDebugInternalFrame2 Interface</span></span>

<span data-ttu-id="9ed30-103">Fournit des informations sur les frames internes, notamment l'adresse et la position de la pile par rapport aux objets ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="9ed30-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ed30-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9ed30-104">Methods</span></span>  
  
|<span data-ttu-id="9ed30-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9ed30-105">Method</span></span>|<span data-ttu-id="9ed30-106">Description</span><span class="sxs-lookup"><span data-stu-id="9ed30-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ed30-107">GetFrameAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="9ed30-107">GetFrameAddress Method</span></span>](icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="9ed30-108">Retourne l’adresse de la pile du frame interne.</span><span class="sxs-lookup"><span data-stu-id="9ed30-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="9ed30-109">IsCloserToLeaf, méthode</span><span class="sxs-lookup"><span data-stu-id="9ed30-109">IsCloserToLeaf Method</span></span>](icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="9ed30-110">Vérifie si le `this` Frame interne est plus proche de la feuille que l’objet ICorDebugFrame spécifié.</span><span class="sxs-lookup"><span data-stu-id="9ed30-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ed30-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="9ed30-111">Remarks</span></span>  

 <span data-ttu-id="9ed30-112">Cette interface étend l’interface ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="9ed30-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ed30-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="9ed30-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ed30-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9ed30-114">Requirements</span></span>  

 <span data-ttu-id="9ed30-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ed30-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed30-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ed30-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ed30-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ed30-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ed30-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed30-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed30-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ed30-119">See also</span></span>

- [<span data-ttu-id="9ed30-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9ed30-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9ed30-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="9ed30-121">Debugging</span></span>](index.md)
