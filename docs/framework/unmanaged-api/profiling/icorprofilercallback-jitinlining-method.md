---
title: ICorProfilerCallback::JITInlining, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
ms.openlocfilehash: 3e13b17fb03530730a78f6889309f1993419574b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866210"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="219b4-102">ICorProfilerCallback::JITInlining, méthode</span><span class="sxs-lookup"><span data-stu-id="219b4-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="219b4-103">Indique au profileur que le compilateur juste-à-temps (JIT) est sur le point d’insérer une fonction en ligne avec une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="219b4-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="219b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="219b4-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="219b4-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="219b4-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="219b4-106">dans ID de la fonction dans laquelle la fonction `calleeId` sera insérée.</span><span class="sxs-lookup"><span data-stu-id="219b4-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="219b4-107">dans ID de la fonction à insérer.</span><span class="sxs-lookup"><span data-stu-id="219b4-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="219b4-108">[out] `true` pour permettre l’insertion ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="219b4-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="219b4-109">Notes</span><span class="sxs-lookup"><span data-stu-id="219b4-109">Remarks</span></span>  
 <span data-ttu-id="219b4-110">Le profileur peut définir `pfShouldInline` sur `false` pour empêcher l’insertion de la fonction `calleeId` dans la fonction `callerId`.</span><span class="sxs-lookup"><span data-stu-id="219b4-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="219b4-111">En outre, le profileur peut désactiver globalement l’insertion inline à l’aide de la COR_PRF_DISABLE_INLINING valeur de l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="219b4-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="219b4-112">Les fonctions insérées Inline ne déclenchent pas d’événements pour l’entrée ou la sortie.</span><span class="sxs-lookup"><span data-stu-id="219b4-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="219b4-113">Par conséquent, le profileur doit définir `pfShouldInline` à `false` afin de produire un graphique des appels précis.</span><span class="sxs-lookup"><span data-stu-id="219b4-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="219b4-114">La définition de `pfShouldInline` sur `false` affecte les performances, car l’insertion inline augmente généralement la vitesse et réduit le nombre d’événements de compilation JIT distincts pour la méthode insérée.</span><span class="sxs-lookup"><span data-stu-id="219b4-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="219b4-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="219b4-115">Requirements</span></span>  
 <span data-ttu-id="219b4-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="219b4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="219b4-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="219b4-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="219b4-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="219b4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="219b4-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="219b4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="219b4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="219b4-120">See also</span></span>

- [<span data-ttu-id="219b4-121">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="219b4-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
