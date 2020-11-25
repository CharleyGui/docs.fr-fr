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
ms.openlocfilehash: d8f2788d63f27aac30cf239b410eecea31f09212
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697881"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="f0675-102">ICorProfilerInfo3::GetThreadStaticAddress2, méthode</span><span class="sxs-lookup"><span data-stu-id="f0675-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>

<span data-ttu-id="f0675-103">Obtient l'adresse du champ statique de thread spécifié qui est dans l'étendue du thread et du domaine d'application spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f0675-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0675-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0675-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0675-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0675-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="f0675-106">dans ID de la classe qui contient le champ statique de thread demandé.</span><span class="sxs-lookup"><span data-stu-id="f0675-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="f0675-107">dans Jeton de métadonnées pour le champ statique de thread demandé.</span><span class="sxs-lookup"><span data-stu-id="f0675-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="f0675-108">[in] ID du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="f0675-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="f0675-109">dans ID du thread qui est l’étendue du champ statique demandé.</span><span class="sxs-lookup"><span data-stu-id="f0675-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="f0675-110">à Pointeur vers l’adresse du champ statique qui est dans le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="f0675-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0675-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="f0675-111">Remarks</span></span>  

 <span data-ttu-id="f0675-112">La `GetThreadStaticAddress2` méthode peut retourner l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="f0675-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="f0675-113">CORPROF_E_DATAINCOMPLETE HRESULT si aucune adresse n’a été assignée au champ statique donné dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="f0675-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="f0675-114">Adresses des objets qui peuvent figurer dans le tas garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f0675-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="f0675-115">Ces adresses peuvent devenir non valides après garbage collection. par conséquent, après garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="f0675-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="f0675-116">Avant la fin du constructeur de classe d’une classe, `GetThreadStaticAddress2` retourne CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques soient déjà initialisés et que les objets de racine garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f0675-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="f0675-117">La méthode [ICorProfilerInfo2 :: GetThreadStaticAddress,](icorprofilerinfo2-getthreadstaticaddress-method.md) est semblable à la `GetThreadStaticAddress2` méthode, mais n’accepte pas d’argument de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="f0675-117">The [ICorProfilerInfo2::GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0675-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f0675-118">Requirements</span></span>  

 <span data-ttu-id="f0675-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0675-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0675-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0675-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0675-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0675-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0675-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0675-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0675-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0675-123">See also</span></span>

- [<span data-ttu-id="f0675-124">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="f0675-124">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="f0675-125">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="f0675-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f0675-126">Profilage</span><span class="sxs-lookup"><span data-stu-id="f0675-126">Profiling</span></span>](index.md)
