---
title: ICorProfilerInfo7, interface
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 4c7e94ffa60bcfaead009e1a8baa9b54b2e8ab7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125054"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="155a3-102">ICorProfilerInfo7, interface</span><span class="sxs-lookup"><span data-stu-id="155a3-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="155a3-103">[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="155a3-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="155a3-104">Sous-classe de [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) qui fournit une méthode pour appliquer des métadonnées nouvellement définies à un module et qui fournit l’accès à un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="155a3-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="155a3-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="155a3-105">Methods</span></span>  
  
|<span data-ttu-id="155a3-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="155a3-106">Method</span></span>|<span data-ttu-id="155a3-107">Description</span><span class="sxs-lookup"><span data-stu-id="155a3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="155a3-108">ApplyMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="155a3-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="155a3-109">Applique les métadonnées nouvellement définies par les méthodes `IMetadataEmit::Define*` à un module spécifié.</span><span class="sxs-lookup"><span data-stu-id="155a3-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="155a3-110">GetInMemorySymbolsLength, méthode</span><span class="sxs-lookup"><span data-stu-id="155a3-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="155a3-111">Retourne la longueur d’un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="155a3-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="155a3-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="155a3-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="155a3-113">Lit les octets d’un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="155a3-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="155a3-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="155a3-114">Requirements</span></span>  
 <span data-ttu-id="155a3-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="155a3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="155a3-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="155a3-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="155a3-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="155a3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="155a3-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="155a3-118">See also</span></span>

- [<span data-ttu-id="155a3-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="155a3-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
