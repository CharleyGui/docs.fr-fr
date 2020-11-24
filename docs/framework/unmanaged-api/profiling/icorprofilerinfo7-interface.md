---
title: ICorProfilerInfo7, interface
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 4acafafa284549fe1b078542a88c0818dcde3038
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686057"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="126bd-102">ICorProfilerInfo7, interface</span><span class="sxs-lookup"><span data-stu-id="126bd-102">ICorProfilerInfo7 Interface</span></span>

<span data-ttu-id="126bd-103">[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="126bd-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="126bd-104">Sous-classe de [ICorProfilerInfo6](icorprofilerinfo6-interface.md) qui fournit une méthode pour appliquer des métadonnées nouvellement définies à un module et qui fournit l’accès à un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="126bd-104">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="126bd-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="126bd-105">Methods</span></span>  
  
|<span data-ttu-id="126bd-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="126bd-106">Method</span></span>|<span data-ttu-id="126bd-107">Description</span><span class="sxs-lookup"><span data-stu-id="126bd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="126bd-108">ApplyMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="126bd-108">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="126bd-109">Applique les métadonnées nouvellement définies par les `IMetadataEmit::Define*` méthodes à un module spécifié.</span><span class="sxs-lookup"><span data-stu-id="126bd-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="126bd-110">GetInMemorySymbolsLength, méthode</span><span class="sxs-lookup"><span data-stu-id="126bd-110">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="126bd-111">Retourne la longueur d’un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="126bd-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="126bd-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="126bd-112">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="126bd-113">Lit les octets d’un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="126bd-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="126bd-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="126bd-114">Requirements</span></span>  

 <span data-ttu-id="126bd-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="126bd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="126bd-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="126bd-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="126bd-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="126bd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126bd-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="126bd-118">See also</span></span>

- [<span data-ttu-id="126bd-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="126bd-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
