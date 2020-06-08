---
title: ICorProfilerInfo7, interface
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 0e9f76717aeff27e863245faac241927e7495076
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495487"
---
# <a name="icorprofilerinfo7-interface"></a><span data-ttu-id="ec6d7-102">ICorProfilerInfo7, interface</span><span class="sxs-lookup"><span data-stu-id="ec6d7-102">ICorProfilerInfo7 Interface</span></span>
<span data-ttu-id="ec6d7-103">[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="ec6d7-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="ec6d7-104">Sous-classe de [ICorProfilerInfo6](icorprofilerinfo6-interface.md) qui fournit une méthode pour appliquer des métadonnées nouvellement définies à un module et qui fournit l’accès à un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="ec6d7-104">A subclass of [ICorProfilerInfo6](icorprofilerinfo6-interface.md) that provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec6d7-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ec6d7-105">Methods</span></span>  
  
|<span data-ttu-id="ec6d7-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="ec6d7-106">Method</span></span>|<span data-ttu-id="ec6d7-107">Description</span><span class="sxs-lookup"><span data-stu-id="ec6d7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec6d7-108">ApplyMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="ec6d7-108">ApplyMetaData Method</span></span>](icorprofilerinfo7-applymetadata-method.md)|<span data-ttu-id="ec6d7-109">Applique les métadonnées nouvellement définies par les `IMetadataEmit::Define*` méthodes à un module spécifié.</span><span class="sxs-lookup"><span data-stu-id="ec6d7-109">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>|  
|[<span data-ttu-id="ec6d7-110">GetInMemorySymbolsLength, méthode</span><span class="sxs-lookup"><span data-stu-id="ec6d7-110">GetInMemorySymbolsLength Method</span></span>](icorprofilerinfo7-getinmemorysymbolslength-method.md)|<span data-ttu-id="ec6d7-111">Retourne la longueur d’un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="ec6d7-111">Returns the length of an in-memory symbol stream.</span></span>|  
|[<span data-ttu-id="ec6d7-112">ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="ec6d7-112">ReadInMemorySymbols</span></span>](icorprofilerinfo7-readinmemorysymbols.md)|<span data-ttu-id="ec6d7-113">Lit les octets d’un flux de symboles en mémoire.</span><span class="sxs-lookup"><span data-stu-id="ec6d7-113">Reads bytes from an in-memory symbol stream.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec6d7-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ec6d7-114">Requirements</span></span>  
 <span data-ttu-id="ec6d7-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec6d7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec6d7-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec6d7-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec6d7-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec6d7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec6d7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec6d7-118">See also</span></span>

- [<span data-ttu-id="ec6d7-119">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="ec6d7-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
