---
title: ICorProfilerInfo::EndInprocDebugging, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7365deb11bf620fcda43e7f04347cfe4685b5a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780243"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="94d7f-102">ICorProfilerInfo::EndInprocDebugging, méthode</span><span class="sxs-lookup"><span data-stu-id="94d7f-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="94d7f-103">Arrête une session de débogage in-process.</span><span class="sxs-lookup"><span data-stu-id="94d7f-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="94d7f-104">Cette méthode est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="94d7f-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94d7f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94d7f-105">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94d7f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="94d7f-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="94d7f-107">[in] Une valeur qui identifie la session de débogage.</span><span class="sxs-lookup"><span data-stu-id="94d7f-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="94d7f-108">Cette valeur doit être la même que celle reçue dans le [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="94d7f-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94d7f-109">Notes</span><span class="sxs-lookup"><span data-stu-id="94d7f-109">Remarks</span></span>  
 <span data-ttu-id="94d7f-110">Vous devez appeler [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) et `EndInprocDebugging` au sein de la même méthode de rappel.</span><span class="sxs-lookup"><span data-stu-id="94d7f-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="94d7f-111">Les services de débogage CLR pris en charge limitée dans le processus de débogage dans les versions 1.0 et 1.1 du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94d7f-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="94d7f-112">Dans le processus de débogage activé un profileur d’utiliser les parties de l’inspection de l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="94d7f-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="94d7f-113">Toutefois, en raison des commentaires client, dans le processus de débogage a été supprimé depuis le .NET Framework version 2.0 et remplacé par un ensemble de fonctionnalités qui sont plus adaptées à l’API de profilage.</span><span class="sxs-lookup"><span data-stu-id="94d7f-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94d7f-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="94d7f-114">Requirements</span></span>  
 <span data-ttu-id="94d7f-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94d7f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94d7f-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="94d7f-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="94d7f-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94d7f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94d7f-118">**Version du .NET framework :** 1.0</span><span class="sxs-lookup"><span data-stu-id="94d7f-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94d7f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94d7f-119">See also</span></span>

- [<span data-ttu-id="94d7f-120">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="94d7f-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
