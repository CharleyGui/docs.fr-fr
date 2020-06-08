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
ms.openlocfilehash: 525fa2efa39909390d874fb97d9f11e647340ea9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496943"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="4349b-102">ICorProfilerInfo2::GetRVAStaticAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="4349b-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="4349b-103">Obtient l’adresse du champ statique d’adresse virtuelle relative (RVA) spécifié.</span><span class="sxs-lookup"><span data-stu-id="4349b-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4349b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4349b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4349b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4349b-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4349b-106">dans ID de la classe qui contient le champ statique RVA demandé.</span><span class="sxs-lookup"><span data-stu-id="4349b-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="4349b-107">dans Jeton de métadonnées pour le champ statique RVA demandé.</span><span class="sxs-lookup"><span data-stu-id="4349b-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="4349b-108">à Pointeur vers l’adresse du champ RVA-static.</span><span class="sxs-lookup"><span data-stu-id="4349b-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4349b-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="4349b-109">Remarks</span></span>  
 <span data-ttu-id="4349b-110">La `GetRVAStaticAddress` méthode peut retourner l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="4349b-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="4349b-111">CORPROF_E_DATAINCOMPLETE HRESULT si aucune adresse n’a été assignée au champ statique donné dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="4349b-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="4349b-112">Adresses des objets qui peuvent figurer dans le tas garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4349b-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="4349b-113">Ces adresses peuvent devenir non valides après garbage collection. par conséquent, après garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="4349b-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="4349b-114">Avant la fin du constructeur de classe d’une classe, `GetRVAStaticAddress` retourne CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques soient déjà initialisés et peuvent être des objets de racine garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4349b-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4349b-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4349b-115">Requirements</span></span>  
 <span data-ttu-id="4349b-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4349b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4349b-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4349b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4349b-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4349b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4349b-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4349b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4349b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4349b-120">See also</span></span>

- [<span data-ttu-id="4349b-121">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="4349b-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="4349b-122">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="4349b-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
