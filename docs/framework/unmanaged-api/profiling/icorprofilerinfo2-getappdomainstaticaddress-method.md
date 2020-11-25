---
title: ICorProfilerInfo2::GetAppDomainStaticAddress, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
ms.openlocfilehash: 271f9f4fd0d85407aedf088ffb524fa6e0398e37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727209"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="1a1b5-102">ICorProfilerInfo2::GetAppDomainStaticAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="1a1b5-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>

<span data-ttu-id="1a1b5-103">Obtient l’adresse du champ statique du domaine d’application spécifié qui est dans la portée du domaine d’application spécifié.</span><span class="sxs-lookup"><span data-stu-id="1a1b5-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a1b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a1b5-104">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a1b5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1a1b5-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="1a1b5-106">dans ID de classe de la classe qui contient le champ statique de domaine d’application demandé.</span><span class="sxs-lookup"><span data-stu-id="1a1b5-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="1a1b5-107">dans Jeton de métadonnées pour le champ statique du domaine d’application demandé.</span><span class="sxs-lookup"><span data-stu-id="1a1b5-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="1a1b5-108">dans ID du domaine d’application qui est l’étendue du champ statique demandé.</span><span class="sxs-lookup"><span data-stu-id="1a1b5-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="1a1b5-109">à Pointeur vers l’adresse du champ statique qui est dans le domaine d’application spécifié.</span><span class="sxs-lookup"><span data-stu-id="1a1b5-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a1b5-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="1a1b5-110">Remarks</span></span>  

 <span data-ttu-id="1a1b5-111">La `GetAppDomainStaticAddress` méthode peut retourner l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1a1b5-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="1a1b5-112">CORPROF_E_DATAINCOMPLETE HRESULT si aucune adresse n’a été assignée au champ statique donné dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="1a1b5-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="1a1b5-113">Adresses des objets qui peuvent figurer dans le tas garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1a1b5-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="1a1b5-114">Ces adresses peuvent devenir non valides après garbage collection. par conséquent, après garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="1a1b5-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="1a1b5-115">Avant la fin du constructeur de classe d’une classe, `GetAppDomainStaticAddress` retourne CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques soient déjà initialisés et que les objets de racine garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1a1b5-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a1b5-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1a1b5-116">Requirements</span></span>  

 <span data-ttu-id="1a1b5-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a1b5-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a1b5-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1a1b5-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1a1b5-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a1b5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a1b5-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a1b5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a1b5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a1b5-121">See also</span></span>

- [<span data-ttu-id="1a1b5-122">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="1a1b5-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="1a1b5-123">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="1a1b5-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
