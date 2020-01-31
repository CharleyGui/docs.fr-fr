---
title: COR_PRF_GC_ROOT_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
ms.openlocfilehash: 0210aca5698cd9c86979c13afd1e622b50d194df
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867180"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a><span data-ttu-id="20df0-102">COR_PRF_GC_ROOT_FLAGS, énumération</span><span class="sxs-lookup"><span data-stu-id="20df0-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>
<span data-ttu-id="20df0-103">Indique une propriété d’une racine de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="20df0-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20df0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20df0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="20df0-105">Members</span><span class="sxs-lookup"><span data-stu-id="20df0-105">Members</span></span>  
  
|<span data-ttu-id="20df0-106">Member</span><span class="sxs-lookup"><span data-stu-id="20df0-106">Member</span></span>|<span data-ttu-id="20df0-107">Description</span><span class="sxs-lookup"><span data-stu-id="20df0-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="20df0-108">La racine empêche un garbage collection de déplacer l’objet.</span><span class="sxs-lookup"><span data-stu-id="20df0-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="20df0-109">La racine n’empêche pas les garbage collection.</span><span class="sxs-lookup"><span data-stu-id="20df0-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="20df0-110">La racine fait référence à un champ de l’objet plutôt qu’à l’objet lui-même.</span><span class="sxs-lookup"><span data-stu-id="20df0-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="20df0-111">La racine empêche garbage collection si le décompte de références de l’objet est une certaine valeur.</span><span class="sxs-lookup"><span data-stu-id="20df0-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20df0-112">Notes</span><span class="sxs-lookup"><span data-stu-id="20df0-112">Remarks</span></span>  
 <span data-ttu-id="20df0-113">`COR_PRF_GC_ROOT_FLAGS` est un masque de données qui fournit des informations supplémentaires sur les racines spéciales.</span><span class="sxs-lookup"><span data-stu-id="20df0-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="20df0-114">Toutefois, toutes les racines ne sont pas spéciales.</span><span class="sxs-lookup"><span data-stu-id="20df0-114">However, not all roots are special.</span></span> <span data-ttu-id="20df0-115">Par exemple, certaines racines ne sont pas des références faibles, des pointeurs intérieurs, des épinglés ou des références comptées.</span><span class="sxs-lookup"><span data-stu-id="20df0-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="20df0-116">Pour ces racines, il n’y a aucun indicateur à transmettre.</span><span class="sxs-lookup"><span data-stu-id="20df0-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="20df0-117">Par conséquent, les méthodes qui utilisent cette énumération, telles que la méthode [ICorProfilerCallback2 :: RootReferences2](icorprofilercallback2-rootreferences2-method.md) , envoient 0 pour le masque de masque des indicateurs, ce qui indique que tous les indicateurs sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="20df0-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20df0-118">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="20df0-118">Requirements</span></span>  
 <span data-ttu-id="20df0-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20df0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20df0-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="20df0-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20df0-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20df0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20df0-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20df0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20df0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20df0-123">See also</span></span>

- [<span data-ttu-id="20df0-124">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="20df0-124">Profiling Enumerations</span></span>](profiling-enumerations.md)
