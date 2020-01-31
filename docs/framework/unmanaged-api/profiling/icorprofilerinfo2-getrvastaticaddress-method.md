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
ms.openlocfilehash: ca64d4f5932fb4a0c0486fee5ca1017a6d3adaf2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868627"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="1c0bb-102">ICorProfilerInfo2::GetRVAStaticAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="1c0bb-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="1c0bb-103">Obtient l’adresse du champ statique d’adresse virtuelle relative (RVA) spécifié.</span><span class="sxs-lookup"><span data-stu-id="1c0bb-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c0bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c0bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c0bb-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="1c0bb-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="1c0bb-106">dans ID de la classe qui contient le champ statique RVA demandé.</span><span class="sxs-lookup"><span data-stu-id="1c0bb-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="1c0bb-107">dans Jeton de métadonnées pour le champ statique RVA demandé.</span><span class="sxs-lookup"><span data-stu-id="1c0bb-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="1c0bb-108">à Pointeur vers l’adresse du champ RVA-static.</span><span class="sxs-lookup"><span data-stu-id="1c0bb-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c0bb-109">Notes</span><span class="sxs-lookup"><span data-stu-id="1c0bb-109">Remarks</span></span>  
 <span data-ttu-id="1c0bb-110">La méthode `GetRVAStaticAddress` peut retourner l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1c0bb-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="1c0bb-111">CORPROF_E_DATAINCOMPLETE HRESULT si aucune adresse n’a été assignée au champ statique donné dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="1c0bb-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="1c0bb-112">Adresses des objets qui peuvent figurer dans le tas garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1c0bb-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="1c0bb-113">Ces adresses peuvent devenir non valides après garbage collection. par conséquent, après garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="1c0bb-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="1c0bb-114">Avant la fin du constructeur de classe d’une classe, `GetRVAStaticAddress` retourne CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques soient déjà initialisés et peuvent être des objets de racine garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1c0bb-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c0bb-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="1c0bb-115">Requirements</span></span>  
 <span data-ttu-id="1c0bb-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c0bb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c0bb-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c0bb-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c0bb-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c0bb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c0bb-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c0bb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c0bb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c0bb-120">See also</span></span>

- [<span data-ttu-id="1c0bb-121">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="1c0bb-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="1c0bb-122">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="1c0bb-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
