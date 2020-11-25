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
ms.openlocfilehash: 067e5093cc3b141936eeec43e77e6e1a9475a8a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727118"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="6b2ce-102">ICorProfilerInfo2::GetContextStaticAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="6b2ce-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>

<span data-ttu-id="6b2ce-103">Obtient l’adresse du champ statique de contexte spécifié qui est dans la portée du contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b2ce-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b2ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b2ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b2ce-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6b2ce-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="6b2ce-106">dans ID de la classe qui contient le champ statique de contexte demandé.</span><span class="sxs-lookup"><span data-stu-id="6b2ce-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="6b2ce-107">dans Jeton de métadonnées pour le champ statique de contexte demandé.</span><span class="sxs-lookup"><span data-stu-id="6b2ce-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="6b2ce-108">dans ID du contexte qui est la portée pour le champ statique de contexte demandé.</span><span class="sxs-lookup"><span data-stu-id="6b2ce-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="6b2ce-109">à Pointeur vers l’adresse du champ statique qui est dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b2ce-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b2ce-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="6b2ce-110">Remarks</span></span>  

 <span data-ttu-id="6b2ce-111">La `GetContextStaticAddress` méthode peut retourner l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="6b2ce-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="6b2ce-112">CORPROF_E_DATAINCOMPLETE HRESULT si aucune adresse n’a été assignée au champ statique donné dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b2ce-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="6b2ce-113">Adresses des objets qui peuvent figurer dans le tas garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6b2ce-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="6b2ce-114">Ces adresses peuvent devenir non valides après garbage collection. par conséquent, après garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="6b2ce-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="6b2ce-115">Avant la fin du constructeur de classe d’une classe, `GetContextStaticAddress` retourne CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques soient déjà initialisés et que les objets de racine garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6b2ce-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b2ce-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6b2ce-116">Requirements</span></span>  

 <span data-ttu-id="6b2ce-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b2ce-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b2ce-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6b2ce-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b2ce-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b2ce-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b2ce-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b2ce-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b2ce-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b2ce-121">See also</span></span>

- [<span data-ttu-id="6b2ce-122">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="6b2ce-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="6b2ce-123">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="6b2ce-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
