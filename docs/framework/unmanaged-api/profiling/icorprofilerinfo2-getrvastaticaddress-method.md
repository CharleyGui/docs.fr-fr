---
title: ICorProfilerInfo2::GetRVAStaticAddress, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
ms.openlocfilehash: ea4f6f129cf2919124b1bef1fd837f2b1e13760e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727053"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="30209-102">ICorProfilerInfo2::GetRVAStaticAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="30209-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>

<span data-ttu-id="30209-103">Obtient l’adresse du champ statique d’adresse virtuelle relative (RVA) spécifié.</span><span class="sxs-lookup"><span data-stu-id="30209-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30209-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30209-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30209-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="30209-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="30209-106">dans ID de la classe qui contient le champ statique RVA demandé.</span><span class="sxs-lookup"><span data-stu-id="30209-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="30209-107">dans Jeton de métadonnées pour le champ statique RVA demandé.</span><span class="sxs-lookup"><span data-stu-id="30209-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="30209-108">à Pointeur vers l’adresse du champ RVA-static.</span><span class="sxs-lookup"><span data-stu-id="30209-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30209-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="30209-109">Remarks</span></span>  

 <span data-ttu-id="30209-110">La `GetRVAStaticAddress` méthode peut retourner l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="30209-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="30209-111">CORPROF_E_DATAINCOMPLETE HRESULT si aucune adresse n’a été assignée au champ statique donné dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="30209-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="30209-112">Adresses des objets qui peuvent figurer dans le tas garbage collection.</span><span class="sxs-lookup"><span data-stu-id="30209-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="30209-113">Ces adresses peuvent devenir non valides après garbage collection. par conséquent, après garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="30209-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="30209-114">Avant la fin du constructeur de classe d’une classe, `GetRVAStaticAddress` retourne CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques soient déjà initialisés et peuvent être des objets de racine garbage collection.</span><span class="sxs-lookup"><span data-stu-id="30209-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30209-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="30209-115">Requirements</span></span>  

 <span data-ttu-id="30209-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30209-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30209-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="30209-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="30209-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30209-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30209-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30209-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30209-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30209-120">See also</span></span>

- [<span data-ttu-id="30209-121">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="30209-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="30209-122">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="30209-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
