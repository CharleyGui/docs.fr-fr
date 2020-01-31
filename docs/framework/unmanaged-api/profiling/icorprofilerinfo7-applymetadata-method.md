---
title: 'ICorProfilerInfo7 :: ApplyMetaData, méthode'
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
ms.openlocfilehash: b9e488a512ad506a8975bfff44ae02cd84c29f74
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861695"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="7ee08-102">ICorProfilerInfo7 :: ApplyMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="7ee08-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="7ee08-103">[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="7ee08-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="7ee08-104">Applique les métadonnées nouvellement définies par les méthodes `IMetadataEmit::Define*` à un module spécifié.</span><span class="sxs-lookup"><span data-stu-id="7ee08-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ee08-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ee08-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ee08-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="7ee08-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="7ee08-107">dans Identificateur du module dont les métadonnées ont été modifiées.</span><span class="sxs-lookup"><span data-stu-id="7ee08-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ee08-108">Notes</span><span class="sxs-lookup"><span data-stu-id="7ee08-108">Remarks</span></span>  
 <span data-ttu-id="7ee08-109">Si des modifications de métadonnées sont apportées après le rappel [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) , vous devez appeler cette méthode avant d’utiliser les nouvelles métadonnées.</span><span class="sxs-lookup"><span data-stu-id="7ee08-109">If metadata changes are made after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="7ee08-110">`ApplyMetaData` prend en charge uniquement l’ajout des types de métadonnées suivants :</span><span class="sxs-lookup"><span data-stu-id="7ee08-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="7ee08-111">`AssemblyRef` les enregistrements que vous créez en appelant [IMetaDataAssemblyEmit ::D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="7ee08-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="7ee08-112">.</span><span class="sxs-lookup"><span data-stu-id="7ee08-112">method.</span></span>  
  
- <span data-ttu-id="7ee08-113">`TypeRef` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7ee08-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="7ee08-114">`TypeSpec` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit :: GetTokenFromTypeSpec,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7ee08-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="7ee08-115">`MemberRef` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7ee08-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="7ee08-116">`MemberSpec` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit2 ::D efinemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7ee08-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="7ee08-117">`UserString` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7ee08-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="7ee08-118">À compter de .NET Core 3,0, `ApplyMetaData` prend également en charge les types suivants :</span><span class="sxs-lookup"><span data-stu-id="7ee08-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="7ee08-119">`TypeDef` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7ee08-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="7ee08-120">`MethodDef` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7ee08-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="7ee08-121">Toutefois, l’ajout de méthodes virtuelles à un type existant n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="7ee08-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="7ee08-122">Les méthodes virtuelles doivent être ajoutées avant le rappel de [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7ee08-122">Virtual methods must be added before the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="7ee08-123">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="7ee08-123">Requirements</span></span>  
 <span data-ttu-id="7ee08-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ee08-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ee08-125">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7ee08-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7ee08-126">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ee08-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ee08-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ee08-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee08-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ee08-128">See also</span></span>

- [<span data-ttu-id="7ee08-129">ICorProfilerInfo7, interface</span><span class="sxs-lookup"><span data-stu-id="7ee08-129">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
