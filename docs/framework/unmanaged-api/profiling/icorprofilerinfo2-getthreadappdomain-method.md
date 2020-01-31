---
title: ICorProfilerInfo2::GetThreadAppDomain, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
ms.openlocfilehash: 7c1ee1c39fbf2dcc1f16df3bc94a235676a216dd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862566"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="d8176-102">ICorProfilerInfo2::GetThreadAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="d8176-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="d8176-103">Obtient l’ID du domaine d’application dans lequel le thread spécifié exécute actuellement du code.</span><span class="sxs-lookup"><span data-stu-id="d8176-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8176-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8176-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8176-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="d8176-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="d8176-106">dans ID spécifiant le thread.</span><span class="sxs-lookup"><span data-stu-id="d8176-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="d8176-107">à Pointeur vers l’ID du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="d8176-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8176-108">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d8176-108">Requirements</span></span>  
 <span data-ttu-id="d8176-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8176-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8176-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8176-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8176-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8176-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8176-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8176-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8176-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8176-113">See also</span></span>

- [<span data-ttu-id="d8176-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="d8176-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="d8176-115">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="d8176-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
