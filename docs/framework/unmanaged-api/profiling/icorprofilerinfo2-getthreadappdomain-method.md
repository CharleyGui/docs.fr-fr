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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fa4b1c45b7bf10d167089f80686f438d54288cf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782227"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="cf232-102">ICorProfilerInfo2::GetThreadAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="cf232-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="cf232-103">Obtient l’ID du domaine d’application dans lequel le thread spécifié est en cours d’exécution code.</span><span class="sxs-lookup"><span data-stu-id="cf232-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf232-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf232-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf232-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf232-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="cf232-106">[in] ID spécifiant le thread.</span><span class="sxs-lookup"><span data-stu-id="cf232-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="cf232-107">[out] Un pointeur vers l’ID du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="cf232-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf232-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cf232-108">Requirements</span></span>  
 <span data-ttu-id="cf232-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf232-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf232-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cf232-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cf232-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf232-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf232-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf232-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf232-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf232-113">See also</span></span>

- [<span data-ttu-id="cf232-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="cf232-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="cf232-115">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="cf232-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
