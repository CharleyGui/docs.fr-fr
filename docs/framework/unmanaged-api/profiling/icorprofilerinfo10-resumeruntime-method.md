---
title: ICorProfilerInfo10::ResumeRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.ResumeRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: cf599e5ded73b09d54c98dcd99f51b30c6a4ba82
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661202"
---
# <a name="icorprofilerinfo10resumeruntime-method"></a><span data-ttu-id="b7519-102">ICorProfilerInfo10:: ResumeRuntime, méthode</span><span class="sxs-lookup"><span data-stu-id="b7519-102">ICorProfilerInfo10::ResumeRuntime Method</span></span>

<span data-ttu-id="b7519-103">Reprend le runtime sans exécuter de GC.</span><span class="sxs-lookup"><span data-stu-id="b7519-103">Resumes the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7519-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7519-104">Syntax</span></span>

```cpp
HRESULT ResumeRuntime();
```

## <a name="requirements"></a><span data-ttu-id="b7519-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b7519-105">Requirements</span></span>

<span data-ttu-id="b7519-106">**Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="b7519-106">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="b7519-107">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b7519-107">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="b7519-108">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7519-108">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b7519-109">**Versions de .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7519-109">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b7519-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7519-110">See also</span></span>

- [<span data-ttu-id="b7519-111">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="b7519-111">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
