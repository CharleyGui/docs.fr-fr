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
ms.openlocfilehash: cc8bdfb1e46e5304227a40f869856f07e1f90bed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707488"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="fc264-102">ICorProfilerInfo::GetInprocInspectionInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="fc264-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>

<span data-ttu-id="fc264-103">Obtient un objet qui peut être interrogé pour une interface « ICorDebugProcess ».</span><span class="sxs-lookup"><span data-stu-id="fc264-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="fc264-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc264-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc264-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc264-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc264-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fc264-106">Parameters</span></span>  

 `ppicd`  
 <span data-ttu-id="fc264-107">objet [out](/cpp/atl/iunknown) qui peut être interrogé pour une `ICorDebugProcess` interface.</span><span class="sxs-lookup"><span data-stu-id="fc264-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc264-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="fc264-108">Remarks</span></span>  

 <span data-ttu-id="fc264-109">L’API de débogage common language runtime (CLR) prenait en charge le débogage in-process limité dans le .NET Framework version 1,0.</span><span class="sxs-lookup"><span data-stu-id="fc264-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="fc264-110">Le débogage en cours de processus permettait à un profileur d’utiliser les parties d’inspection de l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="fc264-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="fc264-111">Suite aux commentaires des clients, le débogage en cours de processus a été supprimé de la .NET Framework dans la version 2,0 et remplacé par un ensemble de fonctionnalités qui est plus conforme à l’API de profilage.</span><span class="sxs-lookup"><span data-stu-id="fc264-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc264-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fc264-112">Requirements</span></span>  

 <span data-ttu-id="fc264-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc264-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc264-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fc264-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fc264-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc264-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc264-116">**Version de .NET Framework :** 1,0</span><span class="sxs-lookup"><span data-stu-id="fc264-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc264-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc264-117">See also</span></span>

- [<span data-ttu-id="fc264-118">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="fc264-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
