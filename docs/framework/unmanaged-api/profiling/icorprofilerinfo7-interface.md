---
title: ICorProfilerInfo7, interface
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: f80f310c10bae33583cb7cd2048ede4f5efbe14c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861747"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="22a0d-102">ICorProfilerInfo7, interface</span><span class="sxs-lookup"><span data-stu-id="22a0d-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="22a0d-103">[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="22a0d-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="22a0d-104">Sous-classe de [ICorProfilerInfo6](icorprofilerinfo6-interface.md) qui fournit une méthode pour appliquer des métadonnées nouvellement définies à un module et qui fournit l’accès à un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="22a0d-104">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="22a0d-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="22a0d-105">Methods</span></span>  
  
|<span data-ttu-id="22a0d-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="22a0d-106">Method</span></span>|<span data-ttu-id="22a0d-107">Description</span><span class="sxs-lookup"><span data-stu-id="22a0d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="22a0d-108">ApplyMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="22a0d-108">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="22a0d-109">Applique les métadonnées nouvellement définies par les méthodes `IMetadataEmit::Define*` à un module spécifié.</span><span class="sxs-lookup"><span data-stu-id="22a0d-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="22a0d-110">GetInMemorySymbolsLength, méthode</span><span class="sxs-lookup"><span data-stu-id="22a0d-110">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="22a0d-111">Retourne la longueur d’un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="22a0d-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="22a0d-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="22a0d-112">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="22a0d-113">Lit les octets d’un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="22a0d-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22a0d-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="22a0d-114">Requirements</span></span>  
 <span data-ttu-id="22a0d-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22a0d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22a0d-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="22a0d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22a0d-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22a0d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a0d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22a0d-118">See also</span></span>

- [<span data-ttu-id="22a0d-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="22a0d-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
