---
title: ICorProfilerCallback::ObjectsAllocatedByClass, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
ms.openlocfilehash: 7176c0f88daad64f793131aca8c6d9fa592a878c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503274"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="23dc2-102">ICorProfilerCallback::ObjectsAllocatedByClass, méthode</span><span class="sxs-lookup"><span data-stu-id="23dc2-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>
<span data-ttu-id="23dc2-103">Notifie le profileur du nombre d’instances de chaque classe spécifiée qui ont été créées depuis la garbage collection la plus récente.</span><span class="sxs-lookup"><span data-stu-id="23dc2-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23dc2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23dc2-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="23dc2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="23dc2-105">Parameters</span></span>  
 `cClassCount`  
 <span data-ttu-id="23dc2-106">dans Taille des `classIds` `cObjects` tableaux et.</span><span class="sxs-lookup"><span data-stu-id="23dc2-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="23dc2-107">dans Tableau d’ID de classe, où chaque ID spécifie une classe avec une ou plusieurs instances.</span><span class="sxs-lookup"><span data-stu-id="23dc2-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="23dc2-108">dans Tableau d’entiers, où chaque entier spécifie le nombre d’instances pour la classe correspondante dans le `classIds` tableau.</span><span class="sxs-lookup"><span data-stu-id="23dc2-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23dc2-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="23dc2-109">Remarks</span></span>  
 <span data-ttu-id="23dc2-110">Les `classIds` `cObjects` tableaux et sont des tableaux parallèles.</span><span class="sxs-lookup"><span data-stu-id="23dc2-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="23dc2-111">Par exemple, `classIds[i]` et `cObjects[i]` référencent la même classe.</span><span class="sxs-lookup"><span data-stu-id="23dc2-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="23dc2-112">Si aucune instance d’une classe n’a été créée depuis la garbage collection précédente, la classe est omise.</span><span class="sxs-lookup"><span data-stu-id="23dc2-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="23dc2-113">Le `ObjectsAllocatedByClass` rappel ne signale pas les objets alloués dans le tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="23dc2-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="23dc2-114">Les nombres indiqués par `ObjectsAllocatedByClass` ne sont que des estimations.</span><span class="sxs-lookup"><span data-stu-id="23dc2-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="23dc2-115">Pour obtenir des nombres exacts, utilisez [ICorProfilerCallback :: ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span><span class="sxs-lookup"><span data-stu-id="23dc2-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="23dc2-116">Le `classIds` tableau peut contenir une ou plusieurs entrées NULL si le `cObjects` tableau correspondant a des types qui déchargent.</span><span class="sxs-lookup"><span data-stu-id="23dc2-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23dc2-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="23dc2-117">Requirements</span></span>  
 <span data-ttu-id="23dc2-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23dc2-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23dc2-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="23dc2-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="23dc2-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23dc2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23dc2-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23dc2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23dc2-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23dc2-122">See also</span></span>

- [<span data-ttu-id="23dc2-123">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="23dc2-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
