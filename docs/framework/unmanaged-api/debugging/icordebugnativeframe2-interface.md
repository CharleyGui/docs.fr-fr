---
title: ICorDebugNativeFrame2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 638ce7933ededf2ff7b03b1c5aed7f6bdbfebc6c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912794"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="fa0cc-102">ICorDebugNativeFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="fa0cc-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="fa0cc-103">Fournit des méthodes qui testent les relations entre frames enfant et parent.</span><span class="sxs-lookup"><span data-stu-id="fa0cc-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa0cc-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="fa0cc-104">Methods</span></span>  
  
|<span data-ttu-id="fa0cc-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="fa0cc-105">Method</span></span>|<span data-ttu-id="fa0cc-106">Description</span><span class="sxs-lookup"><span data-stu-id="fa0cc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa0cc-107">IsChild, méthode</span><span class="sxs-lookup"><span data-stu-id="fa0cc-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="fa0cc-108">Détermine si le frame actuel est un Frame enfant.</span><span class="sxs-lookup"><span data-stu-id="fa0cc-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="fa0cc-109">IsMatchingParentFrame, méthode</span><span class="sxs-lookup"><span data-stu-id="fa0cc-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="fa0cc-110">Détermine si le frame spécifié est le parent du frame actuel.</span><span class="sxs-lookup"><span data-stu-id="fa0cc-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="fa0cc-111">GetStackParameterSize, méthode</span><span class="sxs-lookup"><span data-stu-id="fa0cc-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="fa0cc-112">Retourne la taille cumulée des paramètres sur la pile sur les systèmes d’exploitation x86.</span><span class="sxs-lookup"><span data-stu-id="fa0cc-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa0cc-113">Notes</span><span class="sxs-lookup"><span data-stu-id="fa0cc-113">Remarks</span></span>  
 <span data-ttu-id="fa0cc-114">Cette interface étend logiquement l’interface «ICorDebugNativeFrame».</span><span class="sxs-lookup"><span data-stu-id="fa0cc-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa0cc-115">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="fa0cc-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa0cc-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fa0cc-116">Requirements</span></span>  
 <span data-ttu-id="fa0cc-117">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa0cc-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa0cc-118">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fa0cc-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa0cc-119">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa0cc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa0cc-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa0cc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa0cc-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa0cc-121">See also</span></span>

- [<span data-ttu-id="fa0cc-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="fa0cc-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fa0cc-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="fa0cc-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
