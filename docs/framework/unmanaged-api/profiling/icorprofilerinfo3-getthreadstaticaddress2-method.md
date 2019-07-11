---
title: ICorProfilerInfo3::GetThreadStaticAddress2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85f3ec6c2e0e452d3410437a7ec7cd45eb38cd5a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779850"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="bdf85-102">ICorProfilerInfo3::GetThreadStaticAddress2, méthode</span><span class="sxs-lookup"><span data-stu-id="bdf85-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="bdf85-103">Obtient l'adresse du champ statique de thread spécifié qui est dans l'étendue du thread et du domaine d'application spécifiés.</span><span class="sxs-lookup"><span data-stu-id="bdf85-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdf85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdf85-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdf85-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bdf85-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="bdf85-106">[in] ID de la classe qui contient le champ thread-static demandé.</span><span class="sxs-lookup"><span data-stu-id="bdf85-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="bdf85-107">[in] Le jeton de métadonnées pour le champ statique de thread demandé.</span><span class="sxs-lookup"><span data-stu-id="bdf85-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="bdf85-108">[in] ID du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="bdf85-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="bdf85-109">[in] L’ID du thread qui est la portée pour le champ statique demandé.</span><span class="sxs-lookup"><span data-stu-id="bdf85-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="bdf85-110">[out] Pointeur vers l’adresse du champ statique qui se trouve dans le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="bdf85-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdf85-111">Notes</span><span class="sxs-lookup"><span data-stu-id="bdf85-111">Remarks</span></span>  
 <span data-ttu-id="bdf85-112">Le `GetThreadStaticAddress2` méthode peut retourner l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="bdf85-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="bdf85-113">Un HRESULT CORPROF_E_DATAINCOMPLETE si le champ statique donné n’a pas été assigné une adresse dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="bdf85-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="bdf85-114">Les adresses des objets qui peuvent être dans le tas de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="bdf85-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="bdf85-115">Ces adresses peuvent devenir non valides après le garbage collection, donc après le garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="bdf85-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="bdf85-116">Avant la fin de constructeur de classe d’une classe, `GetThreadStaticAddress2` retournera CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains des champs statiques peuvent déjà être initialisés et utiliser des objets de garbage collection racine.</span><span class="sxs-lookup"><span data-stu-id="bdf85-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="bdf85-117">Le [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) méthode est similaire à la `GetThreadStaticAddress2` (méthode), mais n’accepte ne pas d’argument de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="bdf85-117">The [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdf85-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bdf85-118">Requirements</span></span>  
 <span data-ttu-id="bdf85-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdf85-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdf85-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bdf85-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bdf85-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdf85-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdf85-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdf85-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf85-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdf85-123">See also</span></span>

- [<span data-ttu-id="bdf85-124">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="bdf85-124">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="bdf85-125">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="bdf85-125">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="bdf85-126">Profilage</span><span class="sxs-lookup"><span data-stu-id="bdf85-126">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
