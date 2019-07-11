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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67a680727e824cbe29b9e022e00d661e8694f153
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780564"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="61426-102">ICorProfilerInfo::GetInprocInspectionInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="61426-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="61426-103">Obtient un objet qui peut être interrogé pour une interface « ICorDebugProcess ».</span><span class="sxs-lookup"><span data-stu-id="61426-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="61426-104">Cette méthode est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="61426-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61426-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61426-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61426-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="61426-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="61426-107">[out](/cpp/atl/iunknown) objet qui peut être interrogé pour une `ICorDebugProcess` interface.</span><span class="sxs-lookup"><span data-stu-id="61426-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61426-108">Notes</span><span class="sxs-lookup"><span data-stu-id="61426-108">Remarks</span></span>  
 <span data-ttu-id="61426-109">L’API de débogage du common language runtime (CLR) prise en charge limitée dans le processus de débogage dans le .NET Framework version 1.0.</span><span class="sxs-lookup"><span data-stu-id="61426-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="61426-110">Dans le processus de débogage activé un profileur d’utiliser les parties de l’inspection de l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="61426-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="61426-111">À la suite de commentaires des clients, dans le processus de débogage a été supprimé depuis le .NET Framework version 2.0 et remplacé par un ensemble de fonctionnalités qui sont plus adaptées à l’API de profilage.</span><span class="sxs-lookup"><span data-stu-id="61426-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61426-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="61426-112">Requirements</span></span>  
 <span data-ttu-id="61426-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61426-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61426-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="61426-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="61426-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61426-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61426-116">**Version du .NET framework :** 1.0</span><span class="sxs-lookup"><span data-stu-id="61426-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61426-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61426-117">See also</span></span>

- [<span data-ttu-id="61426-118">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="61426-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
