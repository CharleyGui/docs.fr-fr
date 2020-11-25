---
title: COR_PRF_ASSEMBLY_REFERENCE_INFO, structure
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 7c7d447afcb5a8617aa92212f3325719d5f43bf5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718616"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="b8170-102">COR_PRF_ASSEMBLY_REFERENCE_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="b8170-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>

<span data-ttu-id="b8170-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="b8170-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b8170-104">Fournit au CLR (Common Language Runtime) des informations sur une référence d'assembly qui doit être prise en compte lors d'un parcours de fermeture des références d'assembly.</span><span class="sxs-lookup"><span data-stu-id="b8170-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8170-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8170-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="b8170-106">Membres</span><span class="sxs-lookup"><span data-stu-id="b8170-106">Members</span></span>  
  
|<span data-ttu-id="b8170-107">Membre</span><span class="sxs-lookup"><span data-stu-id="b8170-107">Member</span></span>|<span data-ttu-id="b8170-108">Description</span><span class="sxs-lookup"><span data-stu-id="b8170-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="b8170-109">Un pointeur vers la clé publique ou le jeton de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="b8170-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="b8170-110">Le nombre d'octets dans la clé publique ou le jeton.</span><span class="sxs-lookup"><span data-stu-id="b8170-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="b8170-111">Le nom de l'assembly qui est référencé.</span><span class="sxs-lookup"><span data-stu-id="b8170-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="b8170-112">Un pointeur vers les métadonnées de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="b8170-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="b8170-113">Un pointeur vers un objet blob de hachage.</span><span class="sxs-lookup"><span data-stu-id="b8170-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="b8170-114">Le nombre d'octets de l'objet blob de hachage.</span><span class="sxs-lookup"><span data-stu-id="b8170-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="b8170-115">Les indicateurs de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="b8170-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8170-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="b8170-116">Remarks</span></span>  

 <span data-ttu-id="b8170-117">La structure `COR_PRF_EX_CLAUSE_INFO` est remplie par le profileur quand il déclare des références d'assembly supplémentaires que le CLR (Common Language Runtime) doit prendre en compte lors de la réalisation d'un parcours de fermeture des références d'assembly.</span><span class="sxs-lookup"><span data-stu-id="b8170-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="b8170-118">Si le profileur s’inscrit à la méthode de rappel [ICorProfilerCallback6 :: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , le runtime passe le chemin d’accès et le nom de l’assembly à charger, ainsi qu’un pointeur vers un objet d’interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="b8170-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="b8170-119">Le profileur peut ensuite appeler la méthode [ICorProfilerAssemblyReferenceProvider :: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) avec un `COR_PRF_ASSEMBLY_REFERENCE_INFO` objet pour chaque assembly cible qu’il prévoit de référencer à partir de l’assembly spécifié dans le rappel [ICorProfilerCallback6 :: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b8170-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8170-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b8170-120">Requirements</span></span>  

 <span data-ttu-id="b8170-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8170-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8170-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b8170-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b8170-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8170-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8170-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8170-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8170-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8170-125">See also</span></span>

- [<span data-ttu-id="b8170-126">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="b8170-126">Profiling Structures</span></span>](profiling-structures.md)
- [<span data-ttu-id="b8170-127">GetAssemblyReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="b8170-127">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="b8170-128">AddAssemblyReference, méthode</span><span class="sxs-lookup"><span data-stu-id="b8170-128">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
