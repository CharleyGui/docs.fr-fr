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
ms.openlocfilehash: 7d9fe7d6d5c5af32be22ba19b52e7d40033a6eb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706747"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="8c1d1-102">ICorProfilerInfo::GetClassFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="8c1d1-102">ICorProfilerInfo::GetClassFromToken Method</span></span>

<span data-ttu-id="8c1d1-103">Obtient l’ID de la classe, en fonction du jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8c1d1-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="8c1d1-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c1d1-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="8c1d1-105">Utilisez [ICorProfilerInfo2 :: GetClassFromTokenAndTypeArgs,](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="8c1d1-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c1d1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c1d1-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c1d1-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8c1d1-107">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="8c1d1-108">dans ID du module qui contient la classe.</span><span class="sxs-lookup"><span data-stu-id="8c1d1-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="8c1d1-109">dans Un `mdTypeDef` jeton de métadonnées qui fait référence à la classe.</span><span class="sxs-lookup"><span data-stu-id="8c1d1-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="8c1d1-110">à Pointeur vers l’ID de classe.</span><span class="sxs-lookup"><span data-stu-id="8c1d1-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c1d1-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="8c1d1-111">Remarks</span></span>  

 <span data-ttu-id="8c1d1-112">Cette méthode est obsolète ; Utilisez plutôt `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` pour tous les types.</span><span class="sxs-lookup"><span data-stu-id="8c1d1-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c1d1-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8c1d1-113">Requirements</span></span>  

 <span data-ttu-id="8c1d1-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c1d1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c1d1-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8c1d1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8c1d1-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c1d1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c1d1-117">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="8c1d1-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c1d1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c1d1-118">See also</span></span>

- [<span data-ttu-id="8c1d1-119">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="8c1d1-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
