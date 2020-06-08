---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, méthode
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 8ed3f305deceacb976aeff994db1588f9e1ce1fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495526"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="1a890-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="1a890-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>

<span data-ttu-id="1a890-103">Retourne un énumérateur à toutes les méthodes définies dans un module NGen donné et incluse dans une méthode donnée.</span><span class="sxs-lookup"><span data-stu-id="1a890-103">Returns an enumerator to all the methods that are defined in a given NGen module and inline a given method.</span></span>

## <a name="syntax"></a><span data-ttu-id="1a890-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a890-104">Syntax</span></span>

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a><span data-ttu-id="1a890-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1a890-105">Parameters</span></span>

`inlinersModuleId`\
<span data-ttu-id="1a890-106">dans Identificateur d’un module NGen.</span><span class="sxs-lookup"><span data-stu-id="1a890-106">[in] The identifier of an NGen module.</span></span>

`inlineeModuleId`\
<span data-ttu-id="1a890-107">dans Identificateur d’un module qui définit `inlineeMethodId` .</span><span class="sxs-lookup"><span data-stu-id="1a890-107">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="1a890-108">Pour plus d'informations, consultez la section Remarques.</span><span class="sxs-lookup"><span data-stu-id="1a890-108">See the Remarks section for more information.</span></span>

`inlineeMethodId`\
<span data-ttu-id="1a890-109">dans Identificateur d’une méthode Inline.</span><span class="sxs-lookup"><span data-stu-id="1a890-109">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="1a890-110">Pour plus d'informations, consultez la section Remarques.</span><span class="sxs-lookup"><span data-stu-id="1a890-110">See the Remarks section for more information.</span></span>

`incompleteData`\
<span data-ttu-id="1a890-111">à Indicateur qui signale si `ppEnum` contient toutes les méthodes incorporant une méthode donnée.</span><span class="sxs-lookup"><span data-stu-id="1a890-111">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="1a890-112">Pour plus d'informations, consultez la section Remarques.</span><span class="sxs-lookup"><span data-stu-id="1a890-112">See the Remarks section for more information.</span></span>

`ppEnum`\
<span data-ttu-id="1a890-113">à Pointeur vers l’adresse d’un énumérateur</span><span class="sxs-lookup"><span data-stu-id="1a890-113">[out] A pointer to the address of an enumerator</span></span>

## <a name="remarks"></a><span data-ttu-id="1a890-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="1a890-114">Remarks</span></span>

<span data-ttu-id="1a890-115">`inlineeModuleId`et `inlineeMethodId` forment ensemble l’identificateur complet de la méthode qui peut être Inline.</span><span class="sxs-lookup"><span data-stu-id="1a890-115">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="1a890-116">Par exemple, supposons que module `A` définit une méthode `Simple.Add` :</span><span class="sxs-lookup"><span data-stu-id="1a890-116">For example, assume module `A` defines a method `Simple.Add`:</span></span>

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

<span data-ttu-id="1a890-117">et le module B définit `Fancy.AddTwice` :</span><span class="sxs-lookup"><span data-stu-id="1a890-117">and module B defines `Fancy.AddTwice`:</span></span>

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

<span data-ttu-id="1a890-118">Laisse également supposer que `Fancy.AddTwice` l’appel à est inline `SimpleAdd` .</span><span class="sxs-lookup"><span data-stu-id="1a890-118">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="1a890-119">Un profileur peut utiliser cet énumérateur pour rechercher toutes les méthodes définies dans le module B en ligne `Simple.Add` , et le résultat doit être énuméré `AddTwice` .</span><span class="sxs-lookup"><span data-stu-id="1a890-119">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="1a890-120">`inlineeModuleId`est l’identificateur du module `A` et `inlineeMethodId` est l’identificateur de `Simple.Add(int a, int b)` .</span><span class="sxs-lookup"><span data-stu-id="1a890-120">`inlineeModuleId` is the identifier of module `A`, and `inlineeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>

<span data-ttu-id="1a890-121">Si `incompleteData` a la valeur true après le retour de la fonction, l’énumérateur ne contient pas toutes les méthodes qui entourent une méthode donnée.</span><span class="sxs-lookup"><span data-stu-id="1a890-121">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="1a890-122">Cela peut se produire lorsqu’une ou plusieurs dépendances directes ou indirectes du module Inlines n’ont pas encore été chargées.</span><span class="sxs-lookup"><span data-stu-id="1a890-122">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="1a890-123">Si un profileur a besoin de données précises, il doit réessayer plus tard lorsque d’autres modules sont chargés, de préférence lors du chargement de chaque module.</span><span class="sxs-lookup"><span data-stu-id="1a890-123">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>

<span data-ttu-id="1a890-124">La `EnumNgenModuleMethodsInliningThisMethod` méthode peut être utilisée pour contourner les limitations relatives à l’incorporation de ReJIT.</span><span class="sxs-lookup"><span data-stu-id="1a890-124">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="1a890-125">ReJIT permet à un profileur de modifier l’implémentation d’une méthode, puis de lui créer un nouveau code à la volée.</span><span class="sxs-lookup"><span data-stu-id="1a890-125">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="1a890-126">Par exemple, nous pourrions modifier `Simple.Add` les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1a890-126">For example, we could change `Simple.Add` as follows:</span></span>

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

<span data-ttu-id="1a890-127">Toutefois, étant donné que `Fancy.AddTwice` a déjà été inclus `Simple.Add` , il continue à avoir le même comportement qu’avant.</span><span class="sxs-lookup"><span data-stu-id="1a890-127">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="1a890-128">Pour contourner cette limitation, l’appelant doit rechercher toutes les méthodes de tous les modules qui sont inline `Simple.Add` et utilisent `ICorProfilerInfo5::RequestRejit` sur chacune de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="1a890-128">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="1a890-129">Lorsque les méthodes sont recompilées, elles ont le nouveau comportement de `Simple.Add` au lieu de l’ancien comportement.</span><span class="sxs-lookup"><span data-stu-id="1a890-129">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>

## <a name="requirements"></a><span data-ttu-id="1a890-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1a890-130">Requirements</span></span>

<span data-ttu-id="1a890-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a890-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1a890-132">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1a890-132">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="1a890-133">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a890-133">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="1a890-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a890-134">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1a890-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a890-135">See also</span></span>

- [<span data-ttu-id="1a890-136">ICorProfilerInfo6, interface</span><span class="sxs-lookup"><span data-stu-id="1a890-136">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)
