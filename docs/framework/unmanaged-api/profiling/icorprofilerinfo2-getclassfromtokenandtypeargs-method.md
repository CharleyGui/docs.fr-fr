---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
ms.openlocfilehash: e0663ff122397ba639a0a219e513be2f3f0cbbef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862761"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="a0466-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs, méthode</span><span class="sxs-lookup"><span data-stu-id="a0466-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>
<span data-ttu-id="a0466-103">Obtient le `ClassID` d’un type à l’aide du jeton de métadonnées spécifié et des valeurs de `ClassID` de tous les arguments de type.</span><span class="sxs-lookup"><span data-stu-id="a0466-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0466-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0466-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0466-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="a0466-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="a0466-106">dans ID du module dans lequel le type réside.</span><span class="sxs-lookup"><span data-stu-id="a0466-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="a0466-107">dans `mdTypeDef` jeton de métadonnées qui référence le type.</span><span class="sxs-lookup"><span data-stu-id="a0466-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="a0466-108">dans Nombre de paramètres de type pour le type donné.</span><span class="sxs-lookup"><span data-stu-id="a0466-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="a0466-109">Cette valeur doit être égale à zéro pour les types non génériques.</span><span class="sxs-lookup"><span data-stu-id="a0466-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="a0466-110">dans Tableau de valeurs `ClassID`, chacune d’entre elles étant un argument du type.</span><span class="sxs-lookup"><span data-stu-id="a0466-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="a0466-111">La valeur de `typeArgs` peut être NULL si `cTypeArgs` a la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="a0466-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="a0466-112">à Pointeur vers le `ClassID` du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="a0466-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a0466-113">Notes</span><span class="sxs-lookup"><span data-stu-id="a0466-113">Remarks</span></span>  
 <span data-ttu-id="a0466-114">L’appel de la méthode `GetClassFromTokenAndTypeArgs` avec un `mdTypeRef` au lieu d’un jeton de métadonnées `mdTypeDef` peut avoir des résultats imprévisibles ; les appelants doivent résoudre les `mdTypeRef` en `mdTypeDef` lors de leur passage.</span><span class="sxs-lookup"><span data-stu-id="a0466-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="a0466-115">Si le type n’est pas déjà chargé, l’appel de `GetClassFromTokenAndTypeArgs` déclenchera le chargement, ce qui constitue une opération dangereuse dans de nombreux contextes.</span><span class="sxs-lookup"><span data-stu-id="a0466-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="a0466-116">Par exemple, l’appel de cette méthode pendant le chargement de modules ou d’autres types peut entraîner une boucle infinie, car le runtime tente de charger circulairement des éléments.</span><span class="sxs-lookup"><span data-stu-id="a0466-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="a0466-117">En général, l’utilisation de `GetClassFromTokenAndTypeArgs` est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="a0466-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="a0466-118">Si les profileurs sont intéressés par les événements d’un type particulier, ils doivent stocker les `ModuleID` et `mdTypeDef` de ce type, et utiliser [ICorProfilerInfo2 :: GetClassIDInfo2,](icorprofilerinfo2-getclassidinfo2-method.md) pour vérifier si un `ClassID` donné correspond à celui du type souhaité.</span><span class="sxs-lookup"><span data-stu-id="a0466-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0466-119">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="a0466-119">Requirements</span></span>  
 <span data-ttu-id="a0466-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0466-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0466-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0466-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0466-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0466-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0466-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0466-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0466-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0466-124">See also</span></span>

- [<span data-ttu-id="a0466-125">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="a0466-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="a0466-126">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="a0466-126">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
