---
title: ICorProfilerInfo10::SuspendRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.SuspendRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 8d00718579f44a164cd83e2b05d41f70f1c65785
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452147"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="6abcf-102">ICorProfilerInfo10 :: SuspendRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="6abcf-102">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="6abcf-103">Interrompt le runtime sans exécuter de GC.</span><span class="sxs-lookup"><span data-stu-id="6abcf-103">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="6abcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6abcf-104">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="6abcf-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6abcf-105">Requirements</span></span>

<span data-ttu-id="6abcf-106">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="6abcf-106">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="6abcf-107">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6abcf-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="6abcf-108">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6abcf-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="6abcf-109">**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6abcf-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6abcf-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6abcf-110">See also</span></span>

- [<span data-ttu-id="6abcf-111">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="6abcf-111">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
