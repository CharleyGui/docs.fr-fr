---
title: ICorDebugSymbolProvider2, interface
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 587fc29edce72edca7c811c737d67d96b7cafd27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955467"
---
# <a name="icordebugsymbolprovider2-interface"></a><span data-ttu-id="473d6-102">ICorDebugSymbolProvider2, interface</span><span class="sxs-lookup"><span data-stu-id="473d6-102">ICorDebugSymbolProvider2 Interface</span></span>
<span data-ttu-id="473d6-103">Étend logiquement l’interface [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) pour récupérer des informations supplémentaires sur les symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="473d6-103">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="473d6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="473d6-104">Methods</span></span>  
  
|<span data-ttu-id="473d6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="473d6-105">Method</span></span>|<span data-ttu-id="473d6-106">Description</span><span class="sxs-lookup"><span data-stu-id="473d6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="473d6-107">GetFrameProps, méthode</span><span class="sxs-lookup"><span data-stu-id="473d6-107">GetFrameProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getframeprops-method.md)|<span data-ttu-id="473d6-108">Retourne l'adresse virtuelle relative de départ d'une méthode et le frame parent en fonction d'une adresse virtuelle relative de code.</span><span class="sxs-lookup"><span data-stu-id="473d6-108">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>|  
|[<span data-ttu-id="473d6-109">GetGenericDictionaryInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="473d6-109">GetGenericDictionaryInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|<span data-ttu-id="473d6-110">Récupère un mappage de dictionnaire générique.</span><span class="sxs-lookup"><span data-stu-id="473d6-110">Retrieves a generic dictionary map.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="473d6-111">Notes</span><span class="sxs-lookup"><span data-stu-id="473d6-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="473d6-112">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="473d6-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="473d6-113">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="473d6-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="473d6-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="473d6-114">Requirements</span></span>  
 <span data-ttu-id="473d6-115">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="473d6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="473d6-116">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="473d6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="473d6-117">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="473d6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="473d6-118">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="473d6-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473d6-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="473d6-119">See also</span></span>

- [<span data-ttu-id="473d6-120">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="473d6-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="473d6-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="473d6-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="473d6-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="473d6-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
