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
ms.openlocfilehash: 9c7f01d2e462ad1cb0532be6f369c3118a4deb6a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722490"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="17753-102">ICorProfilerInfo::GetFunctionFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="17753-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>

<span data-ttu-id="17753-103">Obtient l’ID d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="17753-103">Gets the ID of a function.</span></span> <span data-ttu-id="17753-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="17753-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="17753-105">Utilisez la méthode [ICorProfilerInfo2 :: GetFunctionFromTokenAndTypeArgs,](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="17753-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17753-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17753-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="17753-107">Notes</span><span class="sxs-lookup"><span data-stu-id="17753-107">Remarks</span></span>  

 <span data-ttu-id="17753-108">La `GetFunctionFromToken` méthode ne fonctionne pas pour les fonctions ou fonctions génériques dans les types génériques ; elle est désormais obsolète.</span><span class="sxs-lookup"><span data-stu-id="17753-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="17753-109">Utilisez `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` pour toutes les fonctions.</span><span class="sxs-lookup"><span data-stu-id="17753-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17753-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="17753-110">Requirements</span></span>  

 <span data-ttu-id="17753-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17753-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17753-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="17753-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17753-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17753-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17753-114">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="17753-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17753-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17753-115">See also</span></span>

- [<span data-ttu-id="17753-116">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="17753-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
