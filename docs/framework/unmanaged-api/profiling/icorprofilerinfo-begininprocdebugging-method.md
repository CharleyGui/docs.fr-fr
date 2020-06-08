---
title: ICorProfilerInfo::BeginInprocDebugging, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
ms.openlocfilehash: f0b118ef109d0adb17a28b60c091390b8e4280c9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498659"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="5bedd-102">ICorProfilerInfo::BeginInprocDebugging, méthode</span><span class="sxs-lookup"><span data-stu-id="5bedd-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="5bedd-103">Initialise la prise en charge du débogage en cours de processus.</span><span class="sxs-lookup"><span data-stu-id="5bedd-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="5bedd-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5bedd-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bedd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bedd-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bedd-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5bedd-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="5bedd-107">dans Affectez à cette valeur la valeur pour `true` initialiser la prise en charge du débogage pour le thread actuel uniquement ; affectez-lui la valeur `false` pour initialiser la prise en charge du débogage pour tous les threads.</span><span class="sxs-lookup"><span data-stu-id="5bedd-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="5bedd-108">à Pointeur vers une valeur retournée qui identifie la session de débogage.</span><span class="sxs-lookup"><span data-stu-id="5bedd-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bedd-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="5bedd-109">Remarks</span></span>  
 <span data-ttu-id="5bedd-110">Les services de débogage du CLR ont pris en charge le débogage de processus limité dans le .NET Framework versions 1,0 et 1,1.</span><span class="sxs-lookup"><span data-stu-id="5bedd-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="5bedd-111">Le débogage en cours de processus permettait à un profileur d’utiliser les parties d’inspection de l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="5bedd-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="5bedd-112">Toutefois, en raison des commentaires des clients, le débogage en cours de processus a été supprimé de la .NET Framework dans la version 2,0 et remplacé par un ensemble de fonctionnalités qui est plus en ligne avec l’API de profilage.</span><span class="sxs-lookup"><span data-stu-id="5bedd-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bedd-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5bedd-113">Requirements</span></span>  
 <span data-ttu-id="5bedd-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bedd-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bedd-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5bedd-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5bedd-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bedd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bedd-117">**Version de .NET Framework :** 1,0</span><span class="sxs-lookup"><span data-stu-id="5bedd-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bedd-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bedd-118">See also</span></span>

- [<span data-ttu-id="5bedd-119">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="5bedd-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
