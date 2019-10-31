---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, méthode
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 103fe1b6845edfe0a364db979557db63511f6ee3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130385"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="5af99-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="5af99-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="5af99-103">Retourne un énumérateur à toutes les méthodes définies dans un module NGen donné et incluse dans une méthode donnée.</span><span class="sxs-lookup"><span data-stu-id="5af99-103">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="5af99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5af99-104">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="5af99-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5af99-105">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="5af99-106">dans Identificateur d’un module NGen.</span><span class="sxs-lookup"><span data-stu-id="5af99-106">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="5af99-107">dans Identificateur d’un module qui définit `inlineeMethodId`.</span><span class="sxs-lookup"><span data-stu-id="5af99-107">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="5af99-108">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="5af99-108">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="5af99-109">dans Identificateur d’une méthode Inline.</span><span class="sxs-lookup"><span data-stu-id="5af99-109">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="5af99-110">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="5af99-110">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="5af99-111">à Indicateur qui spécifie si `ppEnum` contient toutes les méthodes qui entourent une méthode donnée.</span><span class="sxs-lookup"><span data-stu-id="5af99-111">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="5af99-112">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="5af99-112">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="5af99-113">à Pointeur vers l’adresse d’un énumérateur</span><span class="sxs-lookup"><span data-stu-id="5af99-113">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="5af99-114">Notes</span><span class="sxs-lookup"><span data-stu-id="5af99-114">Remarks</span></span>

<span data-ttu-id="5af99-115">`inlineeModuleId` et `inlineeMethodId` forment ensemble l’identificateur complet de la méthode qui peut être Inline.</span><span class="sxs-lookup"><span data-stu-id="5af99-115">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="5af99-116">Par exemple, supposons que le module `A` définit une méthode `Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="5af99-116">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="5af99-117">et le module B définissent `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="5af99-117">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="5af99-118">Laisse également supposer que `Fancy.AddTwice` Inline l’appel à `SimpleAdd`.</span><span class="sxs-lookup"><span data-stu-id="5af99-118">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="5af99-119">Un profileur peut utiliser cet énumérateur pour rechercher toutes les méthodes définies dans le module B en ligne `Simple.Add`, et le résultat doit énumérer `AddTwice`.</span><span class="sxs-lookup"><span data-stu-id="5af99-119">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="5af99-120">`inlineeModuleId` est l’identificateur de module `A`et `inlineeMethodId` est l’identificateur de `Simple.Add(int a, int b)`.</span><span class="sxs-lookup"><span data-stu-id="5af99-120">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="5af99-121">Si `incompleteData` a la valeur true après le retour de la fonction, l’énumérateur ne contient pas toutes les méthodes qui entourent une méthode donnée.</span><span class="sxs-lookup"><span data-stu-id="5af99-121">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="5af99-122">Cela peut se produire lorsqu’une ou plusieurs dépendances directes ou indirectes du module Inlines n’ont pas encore été chargées.</span><span class="sxs-lookup"><span data-stu-id="5af99-122">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="5af99-123">Si un profileur a besoin de données précises, il doit réessayer plus tard lorsque d’autres modules sont chargés, de préférence lors du chargement de chaque module.</span><span class="sxs-lookup"><span data-stu-id="5af99-123">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="5af99-124">La méthode `EnumNgenModuleMethodsInliningThisMethod` peut être utilisée pour contourner les limitations relatives à l’incorporation de ReJIT.</span><span class="sxs-lookup"><span data-stu-id="5af99-124">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="5af99-125">ReJIT permet à un profileur de modifier l’implémentation d’une méthode, puis de lui créer un nouveau code à la volée.</span><span class="sxs-lookup"><span data-stu-id="5af99-125">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="5af99-126">Par exemple, nous pourrions modifier `Simple.Add` comme suit :</span><span class="sxs-lookup"><span data-stu-id="5af99-126">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="5af99-127">Toutefois, étant donné que `Fancy.AddTwice` a déjà inséré des `Simple.Add`, il continue d’avoir le même comportement qu’avant.</span><span class="sxs-lookup"><span data-stu-id="5af99-127">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="5af99-128">Pour contourner cette limitation, l’appelant doit rechercher toutes les méthodes de tous les modules qui Inline `Simple.Add` et utiliser `ICorProfilerInfo5::RequestRejit` sur chacune de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="5af99-128">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="5af99-129">Lorsque les méthodes sont recompilées, elles ont le nouveau comportement de `Simple.Add` au lieu de l’ancien comportement.</span><span class="sxs-lookup"><span data-stu-id="5af99-129">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="5af99-130">spécifications</span><span class="sxs-lookup"><span data-stu-id="5af99-130">Requirements</span></span>

<span data-ttu-id="5af99-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5af99-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="5af99-132">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5af99-132">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="5af99-133">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5af99-133">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5af99-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5af99-134">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5af99-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5af99-135">See also</span></span>

- [<span data-ttu-id="5af99-136">ICorProfilerInfo6, interface</span><span class="sxs-lookup"><span data-stu-id="5af99-136">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)
