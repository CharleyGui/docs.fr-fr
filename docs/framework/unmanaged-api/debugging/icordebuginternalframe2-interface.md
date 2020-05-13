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
ms.openlocfilehash: ce3ca4745727a1738fdc1a526480d70ffc55ccf8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209901"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="0f373-102">ICorDebugInternalFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="0f373-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="0f373-103">Fournit des informations sur les frames internes, notamment l'adresse et la position de la pile par rapport aux objets ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="0f373-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f373-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0f373-104">Methods</span></span>  
  
|<span data-ttu-id="0f373-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0f373-105">Method</span></span>|<span data-ttu-id="0f373-106">Description</span><span class="sxs-lookup"><span data-stu-id="0f373-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f373-107">GetFrameAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="0f373-107">GetFrameAddress Method</span></span>](icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="0f373-108">Retourne l’adresse de la pile du frame interne.</span><span class="sxs-lookup"><span data-stu-id="0f373-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="0f373-109">IsCloserToLeaf, méthode</span><span class="sxs-lookup"><span data-stu-id="0f373-109">IsCloserToLeaf Method</span></span>](icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="0f373-110">Vérifie si le `this` Frame interne est plus proche de la feuille que l’objet ICorDebugFrame spécifié.</span><span class="sxs-lookup"><span data-stu-id="0f373-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f373-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="0f373-111">Remarks</span></span>  
 <span data-ttu-id="0f373-112">Cette interface étend l’interface ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="0f373-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f373-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="0f373-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f373-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0f373-114">Requirements</span></span>  
 <span data-ttu-id="0f373-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f373-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f373-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f373-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f373-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f373-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f373-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f373-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f373-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f373-119">See also</span></span>

- [<span data-ttu-id="0f373-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0f373-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0f373-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="0f373-121">Debugging</span></span>](index.md)
