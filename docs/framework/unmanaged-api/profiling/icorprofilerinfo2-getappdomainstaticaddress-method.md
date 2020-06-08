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
ms.openlocfilehash: 3dc5f04504cca632892c16d31c92a33935b356e0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497333"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="6e75a-102">ICorProfilerInfo2::GetAppDomainStaticAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="6e75a-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="6e75a-103">Obtient l’adresse du champ statique du domaine d’application spécifié qui est dans la portée du domaine d’application spécifié.</span><span class="sxs-lookup"><span data-stu-id="6e75a-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e75a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e75a-104">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e75a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6e75a-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="6e75a-106">dans ID de classe de la classe qui contient le champ statique de domaine d’application demandé.</span><span class="sxs-lookup"><span data-stu-id="6e75a-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="6e75a-107">dans Jeton de métadonnées pour le champ statique du domaine d’application demandé.</span><span class="sxs-lookup"><span data-stu-id="6e75a-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="6e75a-108">dans ID du domaine d’application qui est l’étendue du champ statique demandé.</span><span class="sxs-lookup"><span data-stu-id="6e75a-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="6e75a-109">à Pointeur vers l’adresse du champ statique qui est dans le domaine d’application spécifié.</span><span class="sxs-lookup"><span data-stu-id="6e75a-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e75a-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="6e75a-110">Remarks</span></span>  
 <span data-ttu-id="6e75a-111">La `GetAppDomainStaticAddress` méthode peut retourner l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="6e75a-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="6e75a-112">CORPROF_E_DATAINCOMPLETE HRESULT si aucune adresse n’a été assignée au champ statique donné dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="6e75a-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="6e75a-113">Adresses des objets qui peuvent figurer dans le tas garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6e75a-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="6e75a-114">Ces adresses peuvent devenir non valides après garbage collection. par conséquent, après garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="6e75a-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="6e75a-115">Avant la fin du constructeur de classe d’une classe, `GetAppDomainStaticAddress` retourne CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques soient déjà initialisés et que les objets de racine garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6e75a-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e75a-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6e75a-116">Requirements</span></span>  
 <span data-ttu-id="6e75a-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e75a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e75a-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6e75a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6e75a-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e75a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e75a-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e75a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e75a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e75a-121">See also</span></span>

- [<span data-ttu-id="6e75a-122">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="6e75a-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="6e75a-123">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="6e75a-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
