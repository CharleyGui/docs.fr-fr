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
ms.openlocfilehash: 27b3037459ac4f995e37515f6e96c28449c80a4f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862943"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="a0f18-102">ICorProfilerInfo2::EnumModuleFrozenObjects, méthode</span><span class="sxs-lookup"><span data-stu-id="a0f18-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="a0f18-103">Obtient un énumérateur qui autorise l’itération sur les objets figés dans le module spécifié. Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="a0f18-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0f18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0f18-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0f18-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="a0f18-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="a0f18-106">dans ID du module qui contient les objets figés à énumérer.</span><span class="sxs-lookup"><span data-stu-id="a0f18-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="a0f18-107">à Pointeur vers l’adresse d’une interface [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) , qui énumère les objets figés.</span><span class="sxs-lookup"><span data-stu-id="a0f18-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0f18-108">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="a0f18-108">Requirements</span></span>  
 <span data-ttu-id="a0f18-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0f18-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0f18-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0f18-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0f18-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0f18-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0f18-112">**Versions de .NET Framework :** 3,5, 3,0 sp1, 3,0, 2,0 sp1, 2,0</span><span class="sxs-lookup"><span data-stu-id="a0f18-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0f18-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0f18-113">See also</span></span>

- [<span data-ttu-id="a0f18-114">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="a0f18-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="a0f18-115">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="a0f18-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
