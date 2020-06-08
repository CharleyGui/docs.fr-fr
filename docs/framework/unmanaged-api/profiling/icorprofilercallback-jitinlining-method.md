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
ms.openlocfilehash: 13ce44c9c7a04b870278bc8926dd9fe5daf10bc3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500011"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="7261d-102">ICorProfilerCallback::JITInlining, méthode</span><span class="sxs-lookup"><span data-stu-id="7261d-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="7261d-103">Indique au profileur que le compilateur juste-à-temps (JIT) est sur le point d’insérer une fonction en ligne avec une autre fonction.</span><span class="sxs-lookup"><span data-stu-id="7261d-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7261d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7261d-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7261d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7261d-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="7261d-106">dans ID de la fonction dans laquelle la `calleeId` fonction sera insérée.</span><span class="sxs-lookup"><span data-stu-id="7261d-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="7261d-107">dans ID de la fonction à insérer.</span><span class="sxs-lookup"><span data-stu-id="7261d-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="7261d-108">[out] `true` pour permettre l’insertion ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="7261d-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7261d-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="7261d-109">Remarks</span></span>  
 <span data-ttu-id="7261d-110">Le profileur peut avoir la valeur pour `pfShouldInline` `false` empêcher l’insertion de la `calleeId` fonction dans la `callerId` fonction.</span><span class="sxs-lookup"><span data-stu-id="7261d-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="7261d-111">En outre, le profileur peut désactiver globalement l’insertion inline à l’aide de la COR_PRF_DISABLE_INLINING valeur de l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="7261d-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="7261d-112">Les fonctions insérées Inline ne déclenchent pas d’événements pour l’entrée ou la sortie.</span><span class="sxs-lookup"><span data-stu-id="7261d-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="7261d-113">Par conséquent, le profileur doit définir sur afin de `pfShouldInline` `false` produire un graphique des appels précis.</span><span class="sxs-lookup"><span data-stu-id="7261d-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="7261d-114">La définition de la valeur `pfShouldInline` sur `false` affecte les performances, car l’insertion inline augmente généralement la vitesse et réduit le nombre d’événements de compilation JIT distincts pour la méthode insérée.</span><span class="sxs-lookup"><span data-stu-id="7261d-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7261d-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7261d-115">Requirements</span></span>  
 <span data-ttu-id="7261d-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7261d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7261d-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7261d-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7261d-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7261d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7261d-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7261d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7261d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7261d-120">See also</span></span>

- [<span data-ttu-id="7261d-121">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="7261d-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
