---
title: ICorProfilerCallback::ModuleUnloadFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
ms.openlocfilehash: fd35f47c004d1ffb235cefe1cd2a1eb2c1fffaef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503313"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="d0de1-102">ICorProfilerCallback::ModuleUnloadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="d0de1-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="d0de1-103">Notifie le profileur qu’un module a terminé le déchargement.</span><span class="sxs-lookup"><span data-stu-id="d0de1-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0de1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0de1-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0de1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d0de1-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="d0de1-106">dans ID du module qui a été déchargé.</span><span class="sxs-lookup"><span data-stu-id="d0de1-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="d0de1-107">dans HRESULT qui indique si le module a été déchargé avec succès.</span><span class="sxs-lookup"><span data-stu-id="d0de1-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0de1-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="d0de1-108">Remarks</span></span>  
 <span data-ttu-id="d0de1-109">La valeur de `moduleId` n’est pas valide pour une demande d’informations après le retour de la méthode [ICorProfilerCallback :: ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d0de1-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="d0de1-110">Certaines parties du déchargement de la classe peuvent continuer après le `ModuleUnloadFinished` rappel.</span><span class="sxs-lookup"><span data-stu-id="d0de1-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="d0de1-111">Un HRESULT d’échec dans `hrStatus` indique un échec.</span><span class="sxs-lookup"><span data-stu-id="d0de1-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="d0de1-112">Toutefois, un HRESULT de réussite dans `hrStatus` indique uniquement que la première partie du déchargement du module a réussi.</span><span class="sxs-lookup"><span data-stu-id="d0de1-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0de1-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d0de1-113">Requirements</span></span>  
 <span data-ttu-id="d0de1-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0de1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0de1-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d0de1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d0de1-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0de1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0de1-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0de1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0de1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0de1-118">See also</span></span>

- [<span data-ttu-id="d0de1-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d0de1-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
