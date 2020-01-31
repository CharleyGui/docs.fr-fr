---
title: ICorProfilerInfo::GetInprocInspectionIThisThread, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
ms.openlocfilehash: 0ab383f0968061667b3580a2058687eecda99dde
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870040"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="c25aa-102">ICorProfilerInfo::GetInprocInspectionIThisThread, méthode</span><span class="sxs-lookup"><span data-stu-id="c25aa-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="c25aa-103">Obtient un objet qui peut être interrogé pour l’interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="c25aa-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="c25aa-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c25aa-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c25aa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c25aa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c25aa-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="c25aa-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="c25aa-107">objet [out](/cpp/atl/iunknown) qui peut être interrogé pour l’interface `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="c25aa-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c25aa-108">Notes</span><span class="sxs-lookup"><span data-stu-id="c25aa-108">Remarks</span></span>  
 <span data-ttu-id="c25aa-109">Les services de débogage common language runtime (CLR) ont pris en charge le débogage in-process limité dans le .NET Framework version 1,0.</span><span class="sxs-lookup"><span data-stu-id="c25aa-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="c25aa-110">Le débogage en cours de processus permettait à un profileur d’utiliser les parties d’inspection de l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="c25aa-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="c25aa-111">Suite aux commentaires des clients, le débogage en cours de processus a été supprimé de la .NET Framework dans la version 2,0 et remplacé par un ensemble de fonctionnalités qui est plus conforme à l’API de profilage.</span><span class="sxs-lookup"><span data-stu-id="c25aa-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c25aa-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="c25aa-112">Requirements</span></span>  
 <span data-ttu-id="c25aa-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c25aa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c25aa-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c25aa-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c25aa-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c25aa-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c25aa-116">**Version de .NET Framework :** 1,0</span><span class="sxs-lookup"><span data-stu-id="c25aa-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c25aa-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c25aa-117">See also</span></span>

- [<span data-ttu-id="c25aa-118">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="c25aa-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
