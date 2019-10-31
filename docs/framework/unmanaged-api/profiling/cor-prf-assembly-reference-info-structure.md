---
title: COR_PRF_ASSEMBLY_REFERENCE_INFO, structure
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: ac7ddeed5694ad0ae6ef3d4a11fcb1fb23755b8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123226"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="8e755-102">COR_PRF_ASSEMBLY_REFERENCE_INFO, structure</span><span class="sxs-lookup"><span data-stu-id="8e755-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="8e755-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="8e755-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8e755-104">Fournit au CLR (Common Language Runtime) des informations sur une référence d'assembly qui doit être prise en compte lors d'un parcours de fermeture des références d'assembly.</span><span class="sxs-lookup"><span data-stu-id="8e755-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e755-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e755-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8e755-106">Membres</span><span class="sxs-lookup"><span data-stu-id="8e755-106">Members</span></span>  
  
|<span data-ttu-id="8e755-107">Membre</span><span class="sxs-lookup"><span data-stu-id="8e755-107">Member</span></span>|<span data-ttu-id="8e755-108">Description</span><span class="sxs-lookup"><span data-stu-id="8e755-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="8e755-109">Un pointeur vers la clé publique ou le jeton de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8e755-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="8e755-110">Le nombre d'octets dans la clé publique ou le jeton.</span><span class="sxs-lookup"><span data-stu-id="8e755-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="8e755-111">Le nom de l'assembly qui est référencé.</span><span class="sxs-lookup"><span data-stu-id="8e755-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="8e755-112">Un pointeur vers les métadonnées de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8e755-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="8e755-113">Un pointeur vers un objet blob de hachage.</span><span class="sxs-lookup"><span data-stu-id="8e755-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="8e755-114">Le nombre d'octets de l'objet blob de hachage.</span><span class="sxs-lookup"><span data-stu-id="8e755-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="8e755-115">Les indicateurs de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8e755-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e755-116">Notes</span><span class="sxs-lookup"><span data-stu-id="8e755-116">Remarks</span></span>  
 <span data-ttu-id="8e755-117">La structure `COR_PRF_EX_CLAUSE_INFO` est remplie par le profileur quand il déclare des références d'assembly supplémentaires que le CLR (Common Language Runtime) doit prendre en compte lors de la réalisation d'un parcours de fermeture des références d'assembly.</span><span class="sxs-lookup"><span data-stu-id="8e755-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="8e755-118">Si le profileur s’inscrit à la méthode de rappel [ICorProfilerCallback6 :: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) , le runtime passe le chemin d’accès et le nom de l’assembly à charger, ainsi qu’un pointeur vers un [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objet d’interface à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8e755-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="8e755-119">Le profileur peut ensuite appeler la méthode [ICorProfilerAssemblyReferenceProvider :: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) avec un objet `COR_PRF_ASSEMBLY_REFERENCE_INFO` pour chaque assembly cible qu’il prévoit de référencer à partir de l’assembly spécifié dans [ICorProfilerCallback6 :: Rappel GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8e755-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e755-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="8e755-120">Requirements</span></span>  
 <span data-ttu-id="8e755-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e755-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e755-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8e755-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8e755-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e755-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e755-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e755-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e755-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e755-125">See also</span></span>

- [<span data-ttu-id="8e755-126">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="8e755-126">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
- [<span data-ttu-id="8e755-127">GetAssemblyReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="8e755-127">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="8e755-128">AddAssemblyReference, méthode</span><span class="sxs-lookup"><span data-stu-id="8e755-128">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
