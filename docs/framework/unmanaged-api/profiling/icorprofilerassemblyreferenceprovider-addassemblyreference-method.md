---
title: ICorProfilerAssemblyReferenceProvider::AddAssemblyReference, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: 2357e5348192db5d41adfe1176300359440aeee3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866726"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="04f86-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference, méthode</span><span class="sxs-lookup"><span data-stu-id="04f86-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="04f86-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="04f86-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="04f86-104">Informe le common language runtime (CLR) d’une référence d’assembly que le profileur prévoit d’ajouter dans le rappel de [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="04f86-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04f86-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04f86-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04f86-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="04f86-106">Parameters</span></span>

- `pAssemblyRefInfo`

  <span data-ttu-id="04f86-107">Pointeur vers une structure [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) qui fournit au CLR des informations sur une référence d’assembly qu’il doit prendre en compte lors de l’exécution d’un parcours de fermeture de référence d’assembly.</span><span class="sxs-lookup"><span data-stu-id="04f86-107">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="04f86-108">Notes</span><span class="sxs-lookup"><span data-stu-id="04f86-108">Remarks</span></span>  
 <span data-ttu-id="04f86-109">Le profileur appelle cette méthode pour chaque assembly cible qu’il prévoit de référencer à partir de l’assembly spécifié dans l’argument `wszAssemblyPath` du rappel [ICorProfilerCallback6 :: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="04f86-109">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="04f86-110">L’objet d’interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) est passé au rappel [ICorProfilerCallback6 :: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) du profileur, avec le chemin d’accès et le nom de l’assembly dans l’argument `wszAssemblyPath`.</span><span class="sxs-lookup"><span data-stu-id="04f86-110">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04f86-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="04f86-111">Requirements</span></span>  
 <span data-ttu-id="04f86-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04f86-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04f86-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="04f86-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04f86-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04f86-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04f86-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04f86-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f86-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04f86-116">See also</span></span>

- [<span data-ttu-id="04f86-117">ICorProfilerAssemblyReferenceProvider, interface</span><span class="sxs-lookup"><span data-stu-id="04f86-117">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="04f86-118">GetAssemblyReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="04f86-118">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="04f86-119">ModuleLoadFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="04f86-119">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
