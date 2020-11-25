---
title: ICorProfilerCallback6::GetAssemblyReferences, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
ms.openlocfilehash: c9e973009f46ef7e554ee2df63493464f4956342
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725480"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a><span data-ttu-id="12e0a-102">ICorProfilerCallback6::GetAssemblyReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="12e0a-102">ICorProfilerCallback6::GetAssemblyReferences Method</span></span>

<span data-ttu-id="12e0a-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="12e0a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="12e0a-104">Notifie le profileur qu'un assembly en est au tout début du chargement, quand le CLR (Common Langage Runtime) effectue un parcours de fermeture de références d'assembly.</span><span class="sxs-lookup"><span data-stu-id="12e0a-104">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12e0a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12e0a-105">Syntax</span></span>  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12e0a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="12e0a-106">Parameters</span></span>  

 `wszAssemblyPath`  
 <span data-ttu-id="12e0a-107">[en entrée] Le chemin d’accès et le nom de l’assembly dont les métadonnées seront modifiées.</span><span class="sxs-lookup"><span data-stu-id="12e0a-107">[in] The path and name of the assembly whose metadata will be modified.</span></span>  
  
 `pAsmRefProvider`  
 <span data-ttu-id="12e0a-108">dans Pointeur vers l’adresse d’une interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) qui spécifie les références d’assembly à ajouter.</span><span class="sxs-lookup"><span data-stu-id="12e0a-108">[in] A pointer to the address of an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface that specifies the assembly references to add.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12e0a-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="12e0a-109">Return Value</span></span>  

 <span data-ttu-id="12e0a-110">Les valeurs retournées depuis ce rappel sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="12e0a-110">Return values from this callback are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12e0a-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="12e0a-111">Remarks</span></span>  

 <span data-ttu-id="12e0a-112">Ce rappel est contrôlé en définissant l’indicateur de masque d’événement [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) lors de l’appel de la méthode [ICorProfilerCallback5 :: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="12e0a-112">This callback is controlled by setting the [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span> <span data-ttu-id="12e0a-113">Si le profileur s’inscrit à la méthode de rappel [ICorProfilerCallback6 :: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , le runtime passe le chemin d’accès et le nom de l’assembly à charger, ainsi qu’un pointeur vers un objet d’interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="12e0a-113">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="12e0a-114">Le profileur peut ensuite appeler la méthode [ICorProfilerAssemblyReferenceProvider :: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) avec un `COR_PRF_ASSEMBLY_REFERENCE_INFO` objet pour chaque assembly cible qu’il prévoit de référencer à partir de l’assembly spécifié dans le `GetAssemblyReferences` rappel.</span><span class="sxs-lookup"><span data-stu-id="12e0a-114">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="12e0a-115">Utilisez le rappel de `GetAssemblyReferences` seulement si le profileur doit modifier les métadonnées d'un assembly pour y ajouter des références d'assembly.</span><span class="sxs-lookup"><span data-stu-id="12e0a-115">Use the `GetAssemblyReferences` callback only if the profiler has to modify an assembly's metadata to add assembly references.</span></span> <span data-ttu-id="12e0a-116">(Notez toutefois que la modification réelle des métadonnées d’un assembly est effectuée dans la méthode de rappel de [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).) Le profileur doit implémenter la `GetAssemblyReferences` méthode de rappel pour informer le Common Language Runtime (CLR) que les références d’assembly seront ajoutées quand le module aura été chargé.</span><span class="sxs-lookup"><span data-stu-id="12e0a-116">(But note that the actual modification of an assembly's metadata is done in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)callback method.) The profiler should implement the `GetAssemblyReferences` callback method to inform the common language runtime (CLR) that assembly references will be added when the module has been loaded.</span></span>  <span data-ttu-id="12e0a-117">Ceci permet de s'assurer que les décisions de partage des assemblys prises par le CLR au cours de cette phase restent valides même si le profileur prévoit de modifier ultérieurement les références d'assembly des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="12e0a-117">This helps ensure that assembly sharing decisions made by the CLR during this early stage remain valid although the profiler plans to modify the metadata assembly references later.</span></span>  <span data-ttu-id="12e0a-118">Cela permet d'éviter certaines instances où les modifications des métadonnées du profileur provoquent une erreur `SECURITY_E_INCOMPATIBLE_SHARE`.</span><span class="sxs-lookup"><span data-stu-id="12e0a-118">This can avoid some instances in which profiler metadata modifications cause an `SECURITY_E_INCOMPATIBLE_SHARE` error.</span></span>  
  
 <span data-ttu-id="12e0a-119">Le profileur utilise l’objet [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) fourni par cette méthode pour ajouter des références d’assembly à l’Explorateur de fermetures de référence d’assembly CLR.</span><span class="sxs-lookup"><span data-stu-id="12e0a-119">The profiler uses the [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object provided by this method to add assembly references to the CLR assembly reference closure walker.</span></span>  <span data-ttu-id="12e0a-120">L’objet [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) doit être utilisé uniquement à partir de ce rappel.</span><span class="sxs-lookup"><span data-stu-id="12e0a-120">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object should be used only from within this callback.</span></span> <span data-ttu-id="12e0a-121">Les appels à la méthode [ICorProfilerAssemblyReferenceProvider :: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) à partir de ce rappel n’entraînent pas de métadonnées modifiées, mais uniquement dans un parcours de fermeture de référence d’assembly modifié.</span><span class="sxs-lookup"><span data-stu-id="12e0a-121">Calls to the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method from this callback don't result in modified metadata, but only in a modified assembly reference closure walk.</span></span> <span data-ttu-id="12e0a-122">Le profileur doit toujours utiliser un objet [IMetaDataAssemblyEmit](../metadata/imetadataassemblyemit-interface.md) pour ajouter explicitement des références d’assembly à partir du rappel [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) pour l’assembly de référence, même s’il implémente le `GetAssemblyReferences` rappel.</span><span class="sxs-lookup"><span data-stu-id="12e0a-122">The profiler will still have to use an [IMetaDataAssemblyEmit](../metadata/imetadataassemblyemit-interface.md) object to explicitly add assembly references from within the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback for the referencing assembly, even if it implements the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="12e0a-123">Le profileur doit être préparé à recevoir des appels en double à ce rappel pour le même assembly et doit répondre de façon identique pour chaque appel dupliqué (en effectuant le même ensemble d’appels [ICorProfilerAssemblyReferenceProvider :: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="12e0a-123">The profiler should be prepared to receive duplicate calls to this callback for the same assembly, and should respond identically for each such duplicate call (by making the same set of [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) calls).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12e0a-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="12e0a-124">Requirements</span></span>  

 <span data-ttu-id="12e0a-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12e0a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12e0a-126">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12e0a-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12e0a-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12e0a-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12e0a-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12e0a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e0a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12e0a-129">See also</span></span>

- [<span data-ttu-id="12e0a-130">ICorProfilerCallback6, interface</span><span class="sxs-lookup"><span data-stu-id="12e0a-130">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)
- [<span data-ttu-id="12e0a-131">ModuleLoadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="12e0a-131">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="12e0a-132">COR_PRF_ASSEMBLY_REFERENCE_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="12e0a-132">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)
- [<span data-ttu-id="12e0a-133">ICorProfilerAssemblyReferenceProvider, interface</span><span class="sxs-lookup"><span data-stu-id="12e0a-133">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
