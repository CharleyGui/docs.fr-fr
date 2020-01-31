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
ms.openlocfilehash: 8a15843e9169442d89996375ee85f62b38f92e30
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864256"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="af782-102">ICorProfilerInfo::EndInprocDebugging, méthode</span><span class="sxs-lookup"><span data-stu-id="af782-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="af782-103">Arrête une session de débogage en cours de processus.</span><span class="sxs-lookup"><span data-stu-id="af782-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="af782-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="af782-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af782-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af782-105">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af782-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="af782-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="af782-107">dans Valeur qui identifie la session de débogage.</span><span class="sxs-lookup"><span data-stu-id="af782-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="af782-108">Cette valeur doit être la même que celle reçue dans la méthode [ICorProfilerInfo :: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) .</span><span class="sxs-lookup"><span data-stu-id="af782-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af782-109">Notes</span><span class="sxs-lookup"><span data-stu-id="af782-109">Remarks</span></span>  
 <span data-ttu-id="af782-110">Vous devez appeler [ICorProfilerInfo :: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) et `EndInprocDebugging` dans la même méthode de rappel.</span><span class="sxs-lookup"><span data-stu-id="af782-110">You must call [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="af782-111">Les services de débogage du CLR ont pris en charge le débogage de processus limité dans le .NET Framework versions 1,0 et 1,1.</span><span class="sxs-lookup"><span data-stu-id="af782-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="af782-112">Le débogage en cours de processus permettait à un profileur d’utiliser les parties d’inspection de l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="af782-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="af782-113">Toutefois, en raison des commentaires des clients, le débogage en cours de processus a été supprimé de la .NET Framework dans la version 2,0 et remplacé par un ensemble de fonctionnalités qui est plus en ligne avec l’API de profilage.</span><span class="sxs-lookup"><span data-stu-id="af782-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af782-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="af782-114">Requirements</span></span>  
 <span data-ttu-id="af782-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af782-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af782-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="af782-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af782-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af782-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af782-118">**Version de .NET Framework :** 1,0</span><span class="sxs-lookup"><span data-stu-id="af782-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af782-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af782-119">See also</span></span>

- [<span data-ttu-id="af782-120">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="af782-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
