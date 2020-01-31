---
title: COR_PRF_GC_ROOT_KIND, énumération
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
ms.openlocfilehash: bff45e6f6f57b95d07ac5073cb70020818cce000
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867163"
---
# <a name="cor_prf_gc_root_kind-enumeration"></a><span data-ttu-id="156e2-102">COR_PRF_GC_ROOT_KIND, énumération</span><span class="sxs-lookup"><span data-stu-id="156e2-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="156e2-103">Indique le type de garbage collection racine exposée par le rappel [ICorProfilerCallback2 :: RootReferences2](icorprofilercallback2-rootreferences2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="156e2-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="156e2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="156e2-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="156e2-105">Members</span><span class="sxs-lookup"><span data-stu-id="156e2-105">Members</span></span>  
  
|<span data-ttu-id="156e2-106">Member</span><span class="sxs-lookup"><span data-stu-id="156e2-106">Member</span></span>|<span data-ttu-id="156e2-107">Description</span><span class="sxs-lookup"><span data-stu-id="156e2-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="156e2-108">La racine est une variable sur la pile.</span><span class="sxs-lookup"><span data-stu-id="156e2-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="156e2-109">La racine est une entrée dans la file d’attente du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="156e2-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="156e2-110">La racine est un handle de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="156e2-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="156e2-111">Le type de racine n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="156e2-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="156e2-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="156e2-112">Requirements</span></span>  
 <span data-ttu-id="156e2-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="156e2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="156e2-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="156e2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="156e2-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="156e2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="156e2-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="156e2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="156e2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="156e2-117">See also</span></span>

- [<span data-ttu-id="156e2-118">Énumérations de profilage</span><span class="sxs-lookup"><span data-stu-id="156e2-118">Profiling Enumerations</span></span>](profiling-enumerations.md)
