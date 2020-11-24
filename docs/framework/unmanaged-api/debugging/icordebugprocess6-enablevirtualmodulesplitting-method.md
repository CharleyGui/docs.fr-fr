---
title: ICorDebugProcess6::EnableVirtualModuleSplitting, méthode
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: 56795c6879d95253383c26c92e060f252a018914
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690204"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a><span data-ttu-id="6d1f3-102">ICorDebugProcess6::EnableVirtualModuleSplitting, méthode</span><span class="sxs-lookup"><span data-stu-id="6d1f3-102">ICorDebugProcess6::EnableVirtualModuleSplitting Method</span></span>

<span data-ttu-id="6d1f3-103">Active ou désactive le fractionnement de module virtuel.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-103">Enables or disables virtual module splitting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d1f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d1f3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d1f3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6d1f3-105">Parameters</span></span>  

 `enableSplitting`  
 <span data-ttu-id="6d1f3-106">`true` pour activer le fractionnement de module virtuel ; `false` pour le désactiver.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-106">`true` to enable virtual module splitting; `false` to disable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d1f3-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="6d1f3-107">Remarks</span></span>  

 <span data-ttu-id="6d1f3-108">Le fractionnement de modules virtuels fait que [ICorDebug](icordebug-interface.md) reconnaît les modules qui ont été fusionnés au cours du processus de génération et les présente sous la forme d’un groupe de modules distincts plutôt qu’un seul module de grande taille.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-108">Virtual module splitting causes [ICorDebug](icordebug-interface.md) to recognize modules that were merged together during the build process and present them as a group of separate modules rather than a single large module.</span></span> <span data-ttu-id="6d1f3-109">Cela modifie le comportement de diverses méthodes [ICorDebug](icordebug-interface.md) décrites ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-109">Doing this changes the behavior of various [ICorDebug](icordebug-interface.md) methods described below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d1f3-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-110">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="6d1f3-111">Cette méthode peut être appelée et la valeur de `enableSplitting` peut être modifiée à tout moment.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-111">This method can be called and the value of `enableSplitting` can be changed at any time.</span></span> <span data-ttu-id="6d1f3-112">Elle n’entraîne pas de modifications fonctionnelles avec état dans un objet [ICorDebug](icordebug-interface.md) , à l’exception de la modification du comportement des méthodes répertoriées dans la section [fractionnement de module virtuel et API de débogage non managé](#APIs) au moment où elles sont appelées.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-112">It does not cause any stateful functional changes in an [ICorDebug](icordebug-interface.md) object, other than altering the behavior of the methods listed in the [Virtual module splitting and the unmanaged debugging APIs](#APIs) section at the time they are called.</span></span> <span data-ttu-id="6d1f3-113">L'utilisation de modules virtuels entraîne une baisse des performances lors de l'appel de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-113">Using virtual modules does incur a performance penalty when calling those methods.</span></span> <span data-ttu-id="6d1f3-114">En outre, une mise en cache significative des métadonnées virtualisées peut être nécessaire pour implémenter correctement les API [IMetaDataImport](../metadata/imetadataimport-interface.md) , et ces caches peuvent être conservés même après la désactivation du fractionnement de module virtuel.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-114">In addition, significant in-memory caching of the virtualized metadata may be required to correctly implement the [IMetaDataImport](../metadata/imetadataimport-interface.md) APIs, and these caches may be retained even after virtual module splitting has been turned off.</span></span>  
  
## <a name="terminology"></a><span data-ttu-id="6d1f3-115">Terminologie</span><span class="sxs-lookup"><span data-stu-id="6d1f3-115">Terminology</span></span>  

 <span data-ttu-id="6d1f3-116">Les termes suivants sont employés dans le cadre du fractionnement de module virtuel :</span><span class="sxs-lookup"><span data-stu-id="6d1f3-116">The following terms are used when describing virtual module splitting:</span></span>  
  
 <span data-ttu-id="6d1f3-117">modules conteneurs ou conteneurs</span><span class="sxs-lookup"><span data-stu-id="6d1f3-117">container modules, or containers</span></span>  
 <span data-ttu-id="6d1f3-118">Modules d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-118">The aggregate modules.</span></span>  
  
 <span data-ttu-id="6d1f3-119">sous-modules ou modules virtuels</span><span class="sxs-lookup"><span data-stu-id="6d1f3-119">sub-modules, or virtual modules</span></span>  
 <span data-ttu-id="6d1f3-120">Modules trouvés dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-120">The modules found in a container.</span></span>  
  
 <span data-ttu-id="6d1f3-121">modules standards</span><span class="sxs-lookup"><span data-stu-id="6d1f3-121">regular modules</span></span>  
 <span data-ttu-id="6d1f3-122">Modules non fusionnés au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-122">Modules that were not merged at build time.</span></span> <span data-ttu-id="6d1f3-123">Ce ne sont ni des modules conteneurs ni des sous-modules.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-123">They are neither container modules nor sub-modules.</span></span>  
  
 <span data-ttu-id="6d1f3-124">Les modules conteneurs et les sous-modules sont représentés par des objets de l'interface ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-124">Both container modules and sub-modules are represented by ICorDebugModule interface objects.</span></span> <span data-ttu-id="6d1f3-125">Toutefois, le comportement de l’interface est légèrement différent dans chaque cas, comme décrit dans la \<x-ref to section> section.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-125">However, the behavior of the interface is slightly different in each case, as the \<x-ref to section> section describes.</span></span>  
  
## <a name="modules-and-assemblies"></a><span data-ttu-id="6d1f3-126">Modules et assemblys</span><span class="sxs-lookup"><span data-stu-id="6d1f3-126">Modules and assemblies</span></span>  

 <span data-ttu-id="6d1f3-127">Les assemblys composés de plusieurs modules ne sont pas pris en charge dans le cadre de la fusion d'assemblys, où il existe une relation un-à-un entre un module et un assembly.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-127">Multi-module assemblies are not supported for assembly merging scenarios, so there is a one-to-one relationship between a module and an assembly.</span></span> <span data-ttu-id="6d1f3-128">Chaque objet ICorDebugModule, représentant un module conteneur ou un sous-module, est associé à un objet ICorDebugAssembly correspondant.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-128">Each ICorDebugModule object, regardless of whether it represents a container module or a sub-module, has a corresponding ICorDebugAssembly object.</span></span> <span data-ttu-id="6d1f3-129">La méthode [ICorDebugModule :: GetAssembly](icordebugmodule-getassembly-method.md) convertit le module en assembly.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-129">The [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) method converts from the module to the assembly.</span></span> <span data-ttu-id="6d1f3-130">Pour mapper dans l’autre sens, la méthode [ICorDebugAssembly :: EnumerateModules,](icordebugassembly-enumeratemodules-method.md) énumère uniquement 1 module.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-130">To map in the other direction, the [ICorDebugAssembly::EnumerateModules](icordebugassembly-enumeratemodules-method.md) method enumerates only 1 module.</span></span> <span data-ttu-id="6d1f3-131">Comme l'assembly et le module forment ici une paire fortement couplée, les termes assembly et module sont largement interchangeables.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-131">Because assembly and module form a tightly coupled pair in this case, the terms assembly and module become largely interchangeable.</span></span>  
  
## <a name="behavioral-differences"></a><span data-ttu-id="6d1f3-132">Différences de comportement</span><span class="sxs-lookup"><span data-stu-id="6d1f3-132">Behavioral differences</span></span>  

 <span data-ttu-id="6d1f3-133">Les modules conteneurs présentent les comportements et caractéristiques suivants :</span><span class="sxs-lookup"><span data-stu-id="6d1f3-133">Container modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="6d1f3-134">Leurs métadonnées pour tous les sous-modules constitutifs sont fusionnées.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-134">Their metadata for all of the constituent sub-modules is merged together.</span></span>  
  
- <span data-ttu-id="6d1f3-135">Leurs noms de type peuvent être altérés.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-135">Their type names may be mangled.</span></span>  
  
- <span data-ttu-id="6d1f3-136">La méthode [ICorDebugModule :: GetName](icordebugmodule-getname-method.md) retourne le chemin d’accès à un module sur disque.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-136">The [ICorDebugModule::GetName](icordebugmodule-getname-method.md) method returns the path to an on-disk module.</span></span>  
  
- <span data-ttu-id="6d1f3-137">La méthode [ICorDebugModule ::](icordebugmodule-getsize-method.md) Desize retourne la taille de cette image.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-137">The [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) method returns the size of that image.</span></span>  
  
- <span data-ttu-id="6d1f3-138">La méthode ICorDebugAssembly3.EnumerateContainedAssemblies répertorie les sous-modules.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-138">The ICorDebugAssembly3.EnumerateContainedAssemblies method lists the sub-modules.</span></span>  
  
- <span data-ttu-id="6d1f3-139">La méthode ICorDebugAssembly3.GetContainerAssembly retourne `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-139">The ICorDebugAssembly3.GetContainerAssembly method returns `S_FALSE`.</span></span>  
  
 <span data-ttu-id="6d1f3-140">Les sous-modules présentent les comportements et caractéristiques suivants :</span><span class="sxs-lookup"><span data-stu-id="6d1f3-140">Sub-modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="6d1f3-141">Ils comportent un jeu réduit de métadonnées qui correspond uniquement à l’assembly d’origine ayant été fusionné.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-141">They have a reduced set of metadata that corresponds only to the original assembly that was merged.</span></span>  
  
- <span data-ttu-id="6d1f3-142">Les noms des métadonnées ne sont pas altérés.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-142">The metadata names are not mangled.</span></span>  
  
- <span data-ttu-id="6d1f3-143">Les jetons de métadonnées ne correspondent généralement pas aux jetons présents dans l’assembly d’origine avant sa fusion au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-143">Metadata tokens are unlikely to match the tokens in the original assembly before it was merged in the build process.</span></span>  
  
- <span data-ttu-id="6d1f3-144">La méthode [ICorDebugModule :: GetName](icordebugmodule-getname-method.md) retourne le nom de l’assembly, et non un chemin d’accès au fichier.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-144">The [ICorDebugModule::GetName](icordebugmodule-getname-method.md) method returns the assembly name, not a file path.</span></span>  
  
- <span data-ttu-id="6d1f3-145">La méthode [ICorDebugModule ::](icordebugmodule-getsize-method.md) Desize retourne la taille d’image non fusionnée d’origine.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-145">The [ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) method returns the original unmerged image size.</span></span>  
  
- <span data-ttu-id="6d1f3-146">La méthode ICorDebugModule3.EnumerateContainedAssemblies retourne `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-146">The ICorDebugModule3.EnumerateContainedAssemblies method returns `S_FALSE`.</span></span>  
  
- <span data-ttu-id="6d1f3-147">La méthode ICorDebugAssembly3.GetContainerAssembly retourne le module conteneur.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-147">The ICorDebugAssembly3.GetContainerAssembly method returns the containing module.</span></span>  
  
## <a name="interfaces-retrieved-from-modules"></a><span data-ttu-id="6d1f3-148">Interfaces récupérées des modules</span><span class="sxs-lookup"><span data-stu-id="6d1f3-148">Interfaces retrieved from modules</span></span>  

 <span data-ttu-id="6d1f3-149">Diverses interfaces peuvent être créées ou récupérées à partir des modules.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-149">A variety of interfaces can be created or retrieved from modules.</span></span> <span data-ttu-id="6d1f3-150">entres autres :</span><span class="sxs-lookup"><span data-stu-id="6d1f3-150">Some of these include:</span></span>  
  
- <span data-ttu-id="6d1f3-151">Objet ICorDebugClass, qui est retourné par la méthode [ICorDebugModule :: GetClassFromToken,](icordebugmodule-getclassfromtoken-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6d1f3-151">An ICorDebugClass object, which is returned by the [ICorDebugModule::GetClassFromToken](icordebugmodule-getclassfromtoken-method.md) method.</span></span>  
  
- <span data-ttu-id="6d1f3-152">Objet ICorDebugAssembly, qui est retourné par la méthode [ICorDebugModule :: GetAssembly](icordebugmodule-getassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6d1f3-152">An ICorDebugAssembly object, which is returned by the [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) method.</span></span>  
  
 <span data-ttu-id="6d1f3-153">Ces objets sont toujours mis en cache par [ICorDebug](icordebug-interface.md)et ils auront la même identité de pointeur, qu’ils aient été créés ou interrogés à partir du module de conteneur ou d’un sous-module.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-153">These objects are always cached by [ICorDebug](icordebug-interface.md), and they will have the same pointer identity regardless of whether they were created or queried from the container module or a sub-module.</span></span> <span data-ttu-id="6d1f3-154">Le sous-module présente une vue filtrée de ces objets mis en cache, pas un cache distinct avec ses propres copies.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-154">The sub-module provides a filtered view of these cached objects, not a separate cache with its own copies.</span></span>  
  
<a name="APIs"></a>

## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a><span data-ttu-id="6d1f3-155">Fractionnement de module virtuel et API de débogage non managées</span><span class="sxs-lookup"><span data-stu-id="6d1f3-155">Virtual module splitting and the unmanaged debugging APIs</span></span>  

 <span data-ttu-id="6d1f3-156">Le tableau suivant montre de quelle manière le fractionnement de module virtuel modifie le comportement d'autres méthodes dans l'API de débogage non managée.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-156">The following table shows how virtual module splitting affects the behavior of other methods in the unmanaged debugging API.</span></span>  
  
|<span data-ttu-id="6d1f3-157">Méthode</span><span class="sxs-lookup"><span data-stu-id="6d1f3-157">Method</span></span>|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[<span data-ttu-id="6d1f3-158">ICorDebugFunction::GetModule</span><span class="sxs-lookup"><span data-stu-id="6d1f3-158">ICorDebugFunction::GetModule</span></span>](icordebugfunction-getmodule-method.md)|<span data-ttu-id="6d1f3-159">Retourne le sous-module dans lequel cette fonction a été initialement définie.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-159">Returns the sub-module this function was originally defined in</span></span>|<span data-ttu-id="6d1f3-160">Retourne le module conteneur dans lequel cette fonction a été fusionnée.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-160">Returns the container module this function was merged into</span></span>|  
|[<span data-ttu-id="6d1f3-161">ICorDebugClass::GetModule</span><span class="sxs-lookup"><span data-stu-id="6d1f3-161">ICorDebugClass::GetModule</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="6d1f3-162">Retourne le sous-module dans lequel cette classe a été initialement définie.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-162">Returns the sub-module this class was originally defined in.</span></span>|<span data-ttu-id="6d1f3-163">Retourne le module conteneur dans lequel cette classe a été fusionnée.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-163">Returns the container module this class was merged into.</span></span>|  
|<span data-ttu-id="6d1f3-164">ICorDebugModuleDebugEvent::GetModule</span><span class="sxs-lookup"><span data-stu-id="6d1f3-164">ICorDebugModuleDebugEvent::GetModule</span></span>|<span data-ttu-id="6d1f3-165">Retourne le module conteneur qui a été chargé.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-165">Returns the container module that was loaded.</span></span> <span data-ttu-id="6d1f3-166">Les sous-modules ne reçoivent pas d'événements de chargement, indépendamment de la valeur de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-166">Sub-modules are not given load events regardless of this setting.</span></span>|<span data-ttu-id="6d1f3-167">Retourne le module conteneur qui a été chargé.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-167">Returns the container module that was loaded.</span></span>|  
|[<span data-ttu-id="6d1f3-168">ICorDebugAppDomain::EnumerateAssemblies</span><span class="sxs-lookup"><span data-stu-id="6d1f3-168">ICorDebugAppDomain::EnumerateAssemblies</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="6d1f3-169">Retourne une liste des sous-assemblys et des assemblys standards. La liste n'inclut pas les assemblys conteneurs.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-169">Returns a list of sub-assemblies and regular assemblies; no container assemblies are included.</span></span> <span data-ttu-id="6d1f3-170">**Remarque :**  S’il manque des symboles dans un assembly de conteneur, aucun de ses sous-assemblys ne sera énuméré.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-170">**Note:**  If any container assembly is missing symbols, none of its sub-assemblies will be enumerated.</span></span> <span data-ttu-id="6d1f3-171">S'il manque des symboles dans un assembly standard, celui-ci pourra ou non être énuméré, en fonction des cas.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-171">If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|<span data-ttu-id="6d1f3-172">Retourne une liste des assemblys conteneurs et des assemblys standards. La liste n'inclut pas les sous-assemblys.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-172">Returns a list of container assemblies and regular assemblies; no sub-assemblies are included.</span></span> <span data-ttu-id="6d1f3-173">**Remarque :**  Si des symboles manquent dans un assembly normal, il est possible qu’il ne soit pas énuméré.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-173">**Note:**  If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|  
|<span data-ttu-id="6d1f3-174">[ICorDebugCode :: GetCode](icordebugcode-getcode-method.md) (en cas de référence au code il uniquement)</span><span class="sxs-lookup"><span data-stu-id="6d1f3-174">[ICorDebugCode::GetCode](icordebugcode-getcode-method.md) (when referring to IL code only)</span></span>|<span data-ttu-id="6d1f3-175">Retourne le code IL qui serait valide dans une image d’assembly avant la fusion.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-175">Returns IL that would be valid in a pre-merge assembly image.</span></span> <span data-ttu-id="6d1f3-176">En particulier, les jetons de métadonnées inline doivent être des jetons TypeRef ou MemberRef quand les types référencés ne sont pas définis dans le module virtuel qui contient le code IL.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-176">Specifically, any inline metadata tokens will correctly be TypeRef or MemberRef tokens when the types being referred to are not defined in the virtual module containing the IL.</span></span> <span data-ttu-id="6d1f3-177">Ces jetons TypeRef ou MemberRef peuvent être recherchés dans l’objet [IMetaDataImport](../metadata/imetadataimport-interface.md) pour l’objet virtuel ICorDebugModule correspondant.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-177">These TypeRef or MemberRef tokens can be looked up in the [IMetaDataImport](../metadata/imetadataimport-interface.md) object for the corresponding virtual ICorDebugModule object.</span></span>|<span data-ttu-id="6d1f3-178">Retourne le code IL dans l’image d’assembly après la fusion.</span><span class="sxs-lookup"><span data-stu-id="6d1f3-178">Returns the IL in the post-merge assembly image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d1f3-179">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6d1f3-179">Requirements</span></span>  

 <span data-ttu-id="6d1f3-180">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d1f3-180">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d1f3-181">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d1f3-181">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d1f3-182">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d1f3-182">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d1f3-183">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d1f3-183">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d1f3-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d1f3-184">See also</span></span>

- [<span data-ttu-id="6d1f3-185">ICorDebugProcess6, interface</span><span class="sxs-lookup"><span data-stu-id="6d1f3-185">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="6d1f3-186">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6d1f3-186">Debugging Interfaces</span></span>](debugging-interfaces.md)
