---
title: ICorDebugILCode2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: 9c1a5cde5a39a334d655d865c5e44a5eb0c1766a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131040"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="cb3d1-102">ICorDebugILCode2, interface</span><span class="sxs-lookup"><span data-stu-id="cb3d1-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="cb3d1-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="cb3d1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="cb3d1-104">Étend logiquement l’interface [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) pour fournir des méthodes qui retournent le jeton pour la signature de variable locale d’une fonction et qui mappent les offsets du langage intermédiaire instrumenté d’un profileur aux DÉCALAGEs il de la méthode d’origine.</span><span class="sxs-lookup"><span data-stu-id="cb3d1-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb3d1-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="cb3d1-105">Methods</span></span>  
  
|<span data-ttu-id="cb3d1-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="cb3d1-106">Method</span></span>|<span data-ttu-id="cb3d1-107">Description</span><span class="sxs-lookup"><span data-stu-id="cb3d1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb3d1-108">GetInstrumentedILMap, méthode</span><span class="sxs-lookup"><span data-stu-id="cb3d1-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="cb3d1-109">Retourne un mappage des décalages du langage intermédiaire instrumenté par le profileur avec les décalages du langage intermédiaire de la méthode d'origine pour cette instance.</span><span class="sxs-lookup"><span data-stu-id="cb3d1-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="cb3d1-110">GetLocalVarSigToken, méthode</span><span class="sxs-lookup"><span data-stu-id="cb3d1-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="cb3d1-111">Obtient le jeton de métadonnées de la signature de variable locale pour la fonction représentée par cette instance.</span><span class="sxs-lookup"><span data-stu-id="cb3d1-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb3d1-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="cb3d1-112">Requirements</span></span>  
 <span data-ttu-id="cb3d1-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb3d1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb3d1-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb3d1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb3d1-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb3d1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb3d1-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb3d1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb3d1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb3d1-117">See also</span></span>

- [<span data-ttu-id="cb3d1-118">ICorDebugILCode, interface</span><span class="sxs-lookup"><span data-stu-id="cb3d1-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="cb3d1-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="cb3d1-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cb3d1-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="cb3d1-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
