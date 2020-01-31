---
title: ICorProfilerInfo::GetInprocInspectionInterface, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
ms.openlocfilehash: 5c9258126c872bd501b4eebc4698b4dded402dfe
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863359"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="a1c13-102">ICorProfilerInfo::GetInprocInspectionInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="a1c13-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="a1c13-103">Obtient un objet qui peut être interrogé pour une interface « ICorDebugProcess ».</span><span class="sxs-lookup"><span data-stu-id="a1c13-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="a1c13-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a1c13-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1c13-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1c13-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1c13-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="a1c13-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="a1c13-107">objet [out](/cpp/atl/iunknown) qui peut être interrogé pour une interface `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="a1c13-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1c13-108">Notes</span><span class="sxs-lookup"><span data-stu-id="a1c13-108">Remarks</span></span>  
 <span data-ttu-id="a1c13-109">L’API de débogage common language runtime (CLR) prenait en charge le débogage in-process limité dans le .NET Framework version 1,0.</span><span class="sxs-lookup"><span data-stu-id="a1c13-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="a1c13-110">Le débogage en cours de processus permettait à un profileur d’utiliser les parties d’inspection de l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="a1c13-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="a1c13-111">Suite aux commentaires des clients, le débogage en cours de processus a été supprimé de la .NET Framework dans la version 2,0 et remplacé par un ensemble de fonctionnalités qui est plus conforme à l’API de profilage.</span><span class="sxs-lookup"><span data-stu-id="a1c13-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1c13-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="a1c13-112">Requirements</span></span>  
 <span data-ttu-id="a1c13-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1c13-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1c13-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1c13-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1c13-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1c13-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1c13-116">**Version de .NET Framework :** 1,0</span><span class="sxs-lookup"><span data-stu-id="a1c13-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c13-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1c13-117">See also</span></span>

- [<span data-ttu-id="a1c13-118">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="a1c13-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
