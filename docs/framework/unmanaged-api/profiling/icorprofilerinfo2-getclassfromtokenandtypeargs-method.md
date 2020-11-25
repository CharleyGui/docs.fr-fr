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
ms.openlocfilehash: 62aad8339b34a4831211a45bd645906d73393d25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727144"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a><span data-ttu-id="1702a-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs, méthode</span><span class="sxs-lookup"><span data-stu-id="1702a-102">ICorProfilerInfo2::GetClassFromTokenAndTypeArgs Method</span></span>

<span data-ttu-id="1702a-103">Obtient le `ClassID` d’un type à l’aide du jeton de métadonnées spécifié et `ClassID` des valeurs de tous les arguments de type.</span><span class="sxs-lookup"><span data-stu-id="1702a-103">Gets the `ClassID` of a type by using the specified metadata token and the `ClassID` values of any type arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1702a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1702a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1702a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1702a-105">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="1702a-106">dans ID du module dans lequel le type réside.</span><span class="sxs-lookup"><span data-stu-id="1702a-106">[in] The ID of the module in which the type resides.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="1702a-107">dans `mdTypeDef` Jeton de métadonnées qui référence le type.</span><span class="sxs-lookup"><span data-stu-id="1702a-107">[in] An `mdTypeDef` metadata token that references the type.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="1702a-108">dans Nombre de paramètres de type pour le type donné.</span><span class="sxs-lookup"><span data-stu-id="1702a-108">[in] The number of type parameters for the given type.</span></span> <span data-ttu-id="1702a-109">Cette valeur doit être égale à zéro pour les types non génériques.</span><span class="sxs-lookup"><span data-stu-id="1702a-109">This value must be zero for non-generic types.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="1702a-110">dans Tableau de `ClassID` valeurs, chacune d’entre elles étant un argument du type.</span><span class="sxs-lookup"><span data-stu-id="1702a-110">[in] An array of `ClassID` values, each of which is an argument of the type.</span></span> <span data-ttu-id="1702a-111">La valeur de `typeArgs` peut être null si `cTypeArgs` a la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="1702a-111">The value of `typeArgs` can be NULL if `cTypeArgs` is set to zero.</span></span>  
  
 `pClassID`  
 <span data-ttu-id="1702a-112">à Pointeur vers le `ClassID` du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="1702a-112">[out] A pointer to the `ClassID` of the specified type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1702a-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="1702a-113">Remarks</span></span>  

 <span data-ttu-id="1702a-114">L’appel `GetClassFromTokenAndTypeArgs` de la méthode avec un `mdTypeRef` au lieu d’un `mdTypeDef` jeton de métadonnées peut avoir des résultats imprévisibles ; les appelants doivent résoudre le `mdTypeRef` en un `mdTypeDef` lors de son passage.</span><span class="sxs-lookup"><span data-stu-id="1702a-114">Calling the `GetClassFromTokenAndTypeArgs` method with an `mdTypeRef` instead of an `mdTypeDef` metadata token can have unpredictable results; callers should resolve the `mdTypeRef` to an `mdTypeDef` when passing it.</span></span>  
  
 <span data-ttu-id="1702a-115">Si le type n’est pas déjà chargé, l’appel de `GetClassFromTokenAndTypeArgs` déclenche le chargement, qui est une opération dangereuse dans de nombreux contextes.</span><span class="sxs-lookup"><span data-stu-id="1702a-115">If the type is not already loaded, calling `GetClassFromTokenAndTypeArgs` will trigger loading, which is a dangerous operation in many contexts.</span></span> <span data-ttu-id="1702a-116">Par exemple, l’appel de cette méthode pendant le chargement de modules ou d’autres types peut entraîner une boucle infinie, car le runtime tente de charger circulairement des éléments.</span><span class="sxs-lookup"><span data-stu-id="1702a-116">For example, calling this method during loading of modules or other types could lead to an infinite loop as the runtime attempts to circularly load things.</span></span>  
  
 <span data-ttu-id="1702a-117">En général, l’utilisation de `GetClassFromTokenAndTypeArgs` est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="1702a-117">In general, use of `GetClassFromTokenAndTypeArgs` is discouraged.</span></span> <span data-ttu-id="1702a-118">Si les profileurs sont intéressés par les événements d’un type particulier, ils doivent stocker les `ModuleID` et `mdTypeDef` de ce type, et utiliser [ICorProfilerInfo2 :: GetClassIDInfo2,](icorprofilerinfo2-getclassidinfo2-method.md) pour vérifier si un donné `ClassID` est celui du type souhaité.</span><span class="sxs-lookup"><span data-stu-id="1702a-118">If profilers are interested in events for a particular type, they should store the `ModuleID` and `mdTypeDef` of that type, and use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) to check whether a given `ClassID` is that of the desired type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1702a-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1702a-119">Requirements</span></span>  

 <span data-ttu-id="1702a-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1702a-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1702a-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1702a-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1702a-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1702a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1702a-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1702a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1702a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1702a-124">See also</span></span>

- [<span data-ttu-id="1702a-125">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="1702a-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="1702a-126">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="1702a-126">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
