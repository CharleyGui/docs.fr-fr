---
title: ICorProfilerInfo2::GetContextStaticAddress, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
ms.openlocfilehash: d99e5000cdd0d7252764554025815dbace2289f4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868679"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="e05d2-102">ICorProfilerInfo2::GetContextStaticAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="e05d2-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="e05d2-103">Obtient l’adresse du champ statique de contexte spécifié qui est dans la portée du contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="e05d2-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e05d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e05d2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e05d2-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e05d2-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e05d2-106">dans ID de la classe qui contient le champ statique de contexte demandé.</span><span class="sxs-lookup"><span data-stu-id="e05d2-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="e05d2-107">dans Jeton de métadonnées pour le champ statique de contexte demandé.</span><span class="sxs-lookup"><span data-stu-id="e05d2-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="e05d2-108">dans ID du contexte qui est la portée pour le champ statique de contexte demandé.</span><span class="sxs-lookup"><span data-stu-id="e05d2-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="e05d2-109">à Pointeur vers l’adresse du champ statique qui est dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="e05d2-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e05d2-110">Notes</span><span class="sxs-lookup"><span data-stu-id="e05d2-110">Remarks</span></span>  
 <span data-ttu-id="e05d2-111">La méthode `GetContextStaticAddress` peut retourner l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e05d2-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="e05d2-112">CORPROF_E_DATAINCOMPLETE HRESULT si aucune adresse n’a été assignée au champ statique donné dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="e05d2-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="e05d2-113">Adresses des objets qui peuvent figurer dans le tas garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e05d2-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="e05d2-114">Ces adresses peuvent devenir non valides après garbage collection. par conséquent, après garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="e05d2-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="e05d2-115">Avant la fin du constructeur de classe d’une classe, `GetContextStaticAddress` retourne CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques soient déjà initialisés et que les objets de racine garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e05d2-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e05d2-116">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e05d2-116">Requirements</span></span>  
 <span data-ttu-id="e05d2-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e05d2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e05d2-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e05d2-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e05d2-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e05d2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e05d2-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e05d2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e05d2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e05d2-121">See also</span></span>

- [<span data-ttu-id="e05d2-122">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="e05d2-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="e05d2-123">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="e05d2-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
