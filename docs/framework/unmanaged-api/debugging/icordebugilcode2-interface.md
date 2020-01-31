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
ms.openlocfilehash: 30008d6cc98f7d0d0501d67e18703ed5a344d43a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794367"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="0bea4-102">ICorDebugILCode2, interface</span><span class="sxs-lookup"><span data-stu-id="0bea4-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="0bea4-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="0bea4-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0bea4-104">Étend logiquement l’interface [ICorDebugILCode](icordebugilcode-interface.md) pour fournir des méthodes qui retournent le jeton pour la signature de variable locale d’une fonction et qui mappent les offsets du langage intermédiaire instrumenté d’un profileur aux DÉCALAGEs il de la méthode d’origine.</span><span class="sxs-lookup"><span data-stu-id="0bea4-104">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0bea4-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0bea4-105">Methods</span></span>  
  
|<span data-ttu-id="0bea4-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="0bea4-106">Method</span></span>|<span data-ttu-id="0bea4-107">Description</span><span class="sxs-lookup"><span data-stu-id="0bea4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0bea4-108">GetInstrumentedILMap, méthode</span><span class="sxs-lookup"><span data-stu-id="0bea4-108">GetInstrumentedILMap Method</span></span>](icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="0bea4-109">Retourne un mappage des décalages du langage intermédiaire instrumenté par le profileur avec les décalages du langage intermédiaire de la méthode d'origine pour cette instance.</span><span class="sxs-lookup"><span data-stu-id="0bea4-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="0bea4-110">GetLocalVarSigToken, méthode</span><span class="sxs-lookup"><span data-stu-id="0bea4-110">GetLocalVarSigToken Method</span></span>](icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="0bea4-111">Obtient le jeton de métadonnées de la signature de variable locale pour la fonction représentée par cette instance.</span><span class="sxs-lookup"><span data-stu-id="0bea4-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0bea4-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="0bea4-112">Requirements</span></span>  
 <span data-ttu-id="0bea4-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bea4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bea4-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bea4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bea4-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bea4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bea4-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bea4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bea4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0bea4-117">See also</span></span>

- [<span data-ttu-id="0bea4-118">ICorDebugILCode, interface</span><span class="sxs-lookup"><span data-stu-id="0bea4-118">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="0bea4-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0bea4-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0bea4-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="0bea4-120">Debugging</span></span>](index.md)
