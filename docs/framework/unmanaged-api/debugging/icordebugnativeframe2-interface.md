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
ms.openlocfilehash: bff6dea0e870cf62734fa583eefa481c594481b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096522"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="2c255-102">ICorDebugNativeFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="2c255-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="2c255-103">Fournit des méthodes qui testent les relations entre frames enfant et parent.</span><span class="sxs-lookup"><span data-stu-id="2c255-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c255-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2c255-104">Methods</span></span>  
  
|<span data-ttu-id="2c255-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="2c255-105">Method</span></span>|<span data-ttu-id="2c255-106">Description</span><span class="sxs-lookup"><span data-stu-id="2c255-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c255-107">IsChild, méthode</span><span class="sxs-lookup"><span data-stu-id="2c255-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="2c255-108">Détermine si le frame actuel est un Frame enfant.</span><span class="sxs-lookup"><span data-stu-id="2c255-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="2c255-109">IsMatchingParentFrame, méthode</span><span class="sxs-lookup"><span data-stu-id="2c255-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="2c255-110">Détermine si le frame spécifié est le parent du frame actuel.</span><span class="sxs-lookup"><span data-stu-id="2c255-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="2c255-111">GetStackParameterSize, méthode</span><span class="sxs-lookup"><span data-stu-id="2c255-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="2c255-112">Retourne la taille cumulée des paramètres sur la pile sur les systèmes d’exploitation x86.</span><span class="sxs-lookup"><span data-stu-id="2c255-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c255-113">Notes</span><span class="sxs-lookup"><span data-stu-id="2c255-113">Remarks</span></span>  
 <span data-ttu-id="2c255-114">Cette interface étend logiquement l’interface « ICorDebugNativeFrame ».</span><span class="sxs-lookup"><span data-stu-id="2c255-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c255-115">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="2c255-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c255-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="2c255-116">Requirements</span></span>  
 <span data-ttu-id="2c255-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c255-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c255-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c255-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c255-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c255-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c255-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c255-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c255-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c255-121">See also</span></span>

- [<span data-ttu-id="2c255-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2c255-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2c255-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="2c255-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
