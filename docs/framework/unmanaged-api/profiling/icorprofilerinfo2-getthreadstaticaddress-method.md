---
title: ICorProfilerInfo2::GetThreadStaticAddress, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
ms.openlocfilehash: 8b9b76fd58d8b3ec5c2d98156b7935051aff074b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731220"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="b25d0-102">ICorProfilerInfo2::GetThreadStaticAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="b25d0-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>

<span data-ttu-id="b25d0-103">Obtient l’adresse du champ statique de thread spécifié qui se trouve dans la portée du thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="b25d0-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b25d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b25d0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b25d0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b25d0-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="b25d0-106">dans ID de la classe qui contient le champ statique de thread demandé.</span><span class="sxs-lookup"><span data-stu-id="b25d0-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="b25d0-107">dans Jeton de métadonnées pour le champ statique de thread demandé.</span><span class="sxs-lookup"><span data-stu-id="b25d0-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="b25d0-108">dans ID du thread qui est l’étendue du champ statique demandé.</span><span class="sxs-lookup"><span data-stu-id="b25d0-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="b25d0-109">à Pointeur vers l’adresse du champ statique qui est dans le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="b25d0-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b25d0-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="b25d0-110">Remarks</span></span>  

 <span data-ttu-id="b25d0-111">La `GetThreadStaticAddress` méthode peut retourner l’un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b25d0-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="b25d0-112">CORPROF_E_DATAINCOMPLETE HRESULT si aucune adresse n’a été assignée au champ statique donné dans le contexte spécifié.</span><span class="sxs-lookup"><span data-stu-id="b25d0-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="b25d0-113">Adresses des objets qui peuvent figurer dans le tas garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b25d0-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="b25d0-114">Ces adresses peuvent devenir non valides après garbage collection. par conséquent, une fois que garbage collection profileurs ne doivent pas supposer qu’ils sont valides.</span><span class="sxs-lookup"><span data-stu-id="b25d0-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="b25d0-115">Avant la fin du constructeur de classe d’une classe, `GetThreadStaticAddress` retourne CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques soient déjà initialisés et que les objets de racine garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b25d0-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b25d0-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b25d0-116">Requirements</span></span>  

 <span data-ttu-id="b25d0-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b25d0-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b25d0-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b25d0-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b25d0-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b25d0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b25d0-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b25d0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b25d0-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b25d0-121">See also</span></span>

- [<span data-ttu-id="b25d0-122">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="b25d0-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="b25d0-123">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="b25d0-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
