---
title: ICorProfilerInfo::SetFunctionIDMapper, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
ms.openlocfilehash: 5272c5bf256f6e21a83470db094ab79317932018
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497476"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="00d23-102">ICorProfilerInfo::SetFunctionIDMapper, méthode</span><span class="sxs-lookup"><span data-stu-id="00d23-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="00d23-103">Spécifie la fonction implémentée par le profileur qui sera appelée pour mapper des valeurs `FunctionID` sur d'autres valeurs, qui sont passées aux raccordements d'entrée/sortie de fonction du profileur.</span><span class="sxs-lookup"><span data-stu-id="00d23-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00d23-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00d23-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="00d23-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="00d23-106">dans Pointeur vers l’implémentation de [FunctionIDMapper](functionidmapper-function.md) qui sera appelée pour mapper les `FunctionID` valeurs à leurs autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="00d23-106">[in] A pointer to the [FunctionIDMapper](functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00d23-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="00d23-107">Remarks</span></span>  
 <span data-ttu-id="00d23-108">Les alternatives pour les `FunctionID` valeurs sont passées aux raccordements d’entrée/sortie de fonction du profileur ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)et [FunctionTailcall2](functiontailcall2-function.md)) qui sont spécifiés par la méthode [ICorProfilerInfo2 :: SetEnterLeaveFunctionHooks2,](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="00d23-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="00d23-109">`FunctionIDMapper`Ne peut être défini qu’une seule fois et il est recommandé de le définir dans le rappel [ICorProfilerCallback :: Initialize](icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="00d23-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00d23-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="00d23-110">Requirements</span></span>  
 <span data-ttu-id="00d23-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00d23-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00d23-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00d23-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00d23-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00d23-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00d23-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00d23-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d23-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00d23-115">See also</span></span>

- [<span data-ttu-id="00d23-116">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="00d23-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
