---
title: ICorProfilerInfo::GetFunctionFromToken, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type:
- apiref
ms.openlocfilehash: 2b2d619c5940376806e9873a528b4f08886593e9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863554"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="1c06d-102">ICorProfilerInfo::GetFunctionFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="1c06d-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="1c06d-103">Obtient l’ID d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="1c06d-103">Gets the ID of a function.</span></span> <span data-ttu-id="1c06d-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1c06d-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="1c06d-105">Utilisez la méthode [ICorProfilerInfo2 :: GetFunctionFromTokenAndTypeArgs,](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="1c06d-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c06d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c06d-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="1c06d-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1c06d-107">Remarks</span></span>  
 <span data-ttu-id="1c06d-108">La méthode `GetFunctionFromToken` ne fonctionne pas pour les fonctions ou fonctions génériques dans les types génériques ; Il est désormais obsolète.</span><span class="sxs-lookup"><span data-stu-id="1c06d-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="1c06d-109">Utilisez `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` pour toutes les fonctions.</span><span class="sxs-lookup"><span data-stu-id="1c06d-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c06d-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="1c06d-110">Requirements</span></span>  
 <span data-ttu-id="1c06d-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c06d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c06d-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c06d-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c06d-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c06d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c06d-114">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="1c06d-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c06d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c06d-115">See also</span></span>

- [<span data-ttu-id="1c06d-116">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="1c06d-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
