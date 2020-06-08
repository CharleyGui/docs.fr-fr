---
title: ICorProfilerInfo2::EnumModuleFrozenObjects, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.EnumModuleFrozenObjects
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type:
- apiref
ms.openlocfilehash: 1fe44f8f84c079e920c8c82fb9d52d1980d3b852
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497203"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="3db52-102">ICorProfilerInfo2::EnumModuleFrozenObjects, méthode</span><span class="sxs-lookup"><span data-stu-id="3db52-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="3db52-103">Obtient un énumérateur qui autorise l’itération sur les objets figés dans le module spécifié. Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="3db52-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3db52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3db52-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3db52-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3db52-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="3db52-106">dans ID du module qui contient les objets figés à énumérer.</span><span class="sxs-lookup"><span data-stu-id="3db52-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="3db52-107">à Pointeur vers l’adresse d’une interface [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) , qui énumère les objets figés.</span><span class="sxs-lookup"><span data-stu-id="3db52-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3db52-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3db52-108">Requirements</span></span>  
 <span data-ttu-id="3db52-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3db52-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3db52-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3db52-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3db52-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3db52-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3db52-112">**Versions de .NET Framework :** 3,5, 3,0 sp1, 3,0, 2,0 sp1, 2,0</span><span class="sxs-lookup"><span data-stu-id="3db52-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db52-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3db52-113">See also</span></span>

- [<span data-ttu-id="3db52-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="3db52-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="3db52-115">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="3db52-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
