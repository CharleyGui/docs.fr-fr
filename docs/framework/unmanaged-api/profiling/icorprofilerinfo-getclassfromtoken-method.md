---
title: ICorProfilerInfo::GetClassFromToken, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
ms.openlocfilehash: 841953625235406f013e9f140ad91c7b65680e47
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863951"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="d28cf-102">ICorProfilerInfo::GetClassFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="d28cf-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="d28cf-103">Obtient l’ID de la classe, en fonction du jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d28cf-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="d28cf-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d28cf-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="d28cf-105">Utilisez [ICorProfilerInfo2 :: GetClassFromTokenAndTypeArgs,](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="d28cf-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d28cf-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d28cf-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d28cf-107">Parameters</span><span class="sxs-lookup"><span data-stu-id="d28cf-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="d28cf-108">dans ID du module qui contient la classe.</span><span class="sxs-lookup"><span data-stu-id="d28cf-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="d28cf-109">dans `mdTypeDef` jeton de métadonnées qui fait référence à la classe.</span><span class="sxs-lookup"><span data-stu-id="d28cf-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="d28cf-110">à Pointeur vers l’ID de classe.</span><span class="sxs-lookup"><span data-stu-id="d28cf-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d28cf-111">Notes</span><span class="sxs-lookup"><span data-stu-id="d28cf-111">Remarks</span></span>  
 <span data-ttu-id="d28cf-112">Cette méthode est obsolète ; Utilisez plutôt `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` pour tous les types.</span><span class="sxs-lookup"><span data-stu-id="d28cf-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d28cf-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d28cf-113">Requirements</span></span>  
 <span data-ttu-id="d28cf-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d28cf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d28cf-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d28cf-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d28cf-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d28cf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d28cf-117">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="d28cf-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d28cf-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d28cf-118">See also</span></span>

- [<span data-ttu-id="d28cf-119">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="d28cf-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
