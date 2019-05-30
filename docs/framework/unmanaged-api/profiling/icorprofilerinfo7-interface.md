---
title: ICorProfilerInfo7, interface
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a734bfdef89d4f8f9459f49a3ce2cee83faef9f6
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66250984"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="45f07-102">ICorProfilerInfo7, interface</span><span class="sxs-lookup"><span data-stu-id="45f07-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="45f07-103">[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="45f07-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="45f07-104">Une sous-classe de [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) qui fournit une méthode pour appliquer qui vient d’être défini des métadonnées à un module et qui fournit l’accès à un flux de symbole d’en mémoire.</span><span class="sxs-lookup"><span data-stu-id="45f07-104">A subclass of [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45f07-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="45f07-105">Methods</span></span>  
  
|<span data-ttu-id="45f07-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="45f07-106">Method</span></span>|<span data-ttu-id="45f07-107">Description</span><span class="sxs-lookup"><span data-stu-id="45f07-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45f07-108">ApplyMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="45f07-108">ApplyMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="45f07-109">Applique les métadonnées qui vient d’être définie par le `IMetadataEmit::Define*` méthodes à un module spécifié.</span><span class="sxs-lookup"><span data-stu-id="45f07-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="45f07-110">GetInMemorySymbolsLength, méthode</span><span class="sxs-lookup"><span data-stu-id="45f07-110">GetInMemorySymbolsLength Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="45f07-111">Retourne la longueur d’un flux de symbole d’en mémoire.</span><span class="sxs-lookup"><span data-stu-id="45f07-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="45f07-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="45f07-112">ReadInMemorySymbols</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="45f07-113">Lit les octets à partir d’un flux de symbole d’en mémoire.</span><span class="sxs-lookup"><span data-stu-id="45f07-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45f07-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="45f07-114">Requirements</span></span>  
 <span data-ttu-id="45f07-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45f07-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45f07-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45f07-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45f07-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45f07-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45f07-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45f07-118">See also</span></span>

- [<span data-ttu-id="45f07-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="45f07-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
