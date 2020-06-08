---
title: ICorProfilerInfo8::IsFunctionDynamic
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: c88279d361ea78a2e910c4621e92c500902d9124
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495123"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="a6e10-102">ICorProfilerInfo8 :: IsFunctionDynamic, méthode</span><span class="sxs-lookup"><span data-stu-id="a6e10-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="a6e10-103">Détermine si une fonction n’a pas de métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="a6e10-103">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="a6e10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6e10-104">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="a6e10-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a6e10-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="a6e10-106">\[in] `FunctionID` qui identifie la fonction en question.</span><span class="sxs-lookup"><span data-stu-id="a6e10-106">\[in]  The `FunctionID` that identifies the function in question.</span></span>

- `isDynamic`

  <span data-ttu-id="a6e10-107">\[out] pointeur vers un `BOOL` qui contient une valeur indiquant si la fonction n’a pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a6e10-107">\[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6e10-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="a6e10-108">Remarks</span></span>

<span data-ttu-id="a6e10-109">Une fonction est considérée comme dynamique si elle n’a pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a6e10-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="a6e10-110">Certaines méthodes telles que les stubs IL ou les méthodes LCG n’ont pas de métadonnées associées qui peuvent être récupérées à l’aide des API IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="a6e10-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="a6e10-111">Ces méthodes peuvent être rencontrées par les profileurs par le biais de pointeurs d’instruction ou en écoutant [ICorProfilerCallback ::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="a6e10-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="a6e10-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a6e10-112">Requirements</span></span>

<span data-ttu-id="a6e10-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6e10-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a6e10-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6e10-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a6e10-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6e10-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a6e10-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a6e10-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a6e10-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6e10-117">See also</span></span>

- [<span data-ttu-id="a6e10-118">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="a6e10-118">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
