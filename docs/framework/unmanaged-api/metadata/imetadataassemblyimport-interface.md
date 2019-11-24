---
title: IMetaDataAssemblyImport, interface
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
ms.openlocfilehash: 289e26868ff2eb9e1d97cf084e9a888815062ea4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436305"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="48cea-102">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="48cea-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="48cea-103">Fournit des méthodes pour accéder au contenu d'un manifeste d'assembly et l'examiner.</span><span class="sxs-lookup"><span data-stu-id="48cea-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48cea-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="48cea-104">Methods</span></span>  
  
|<span data-ttu-id="48cea-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-105">Method</span></span>|<span data-ttu-id="48cea-106">Description</span><span class="sxs-lookup"><span data-stu-id="48cea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48cea-107">CloseEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="48cea-108">Releases the handle to the specified enumerator.</span><span class="sxs-lookup"><span data-stu-id="48cea-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="48cea-109">EnumAssemblyRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="48cea-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="48cea-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="48cea-111">EnumExportedTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="48cea-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="48cea-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="48cea-113">EnumFiles, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="48cea-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="48cea-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="48cea-115">EnumManifestResources, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="48cea-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="48cea-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="48cea-117">FindAssembliesByName, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="48cea-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span><span class="sxs-lookup"><span data-stu-id="48cea-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="48cea-119">FindExportedTypeByName, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="48cea-120">Gets an `mdExportedType` token for the COM type with the specified name.</span><span class="sxs-lookup"><span data-stu-id="48cea-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="48cea-121">FindManifestResourceByName, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="48cea-122">Gets an `mdManifestResource` token for the resource with the specified name.</span><span class="sxs-lookup"><span data-stu-id="48cea-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="48cea-123">GetAssemblyFromScope, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="48cea-124">Gets the token for the assembly in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="48cea-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="48cea-125">GetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="48cea-126">Gets the property settings of the specified assembly.</span><span class="sxs-lookup"><span data-stu-id="48cea-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="48cea-127">GetAssemblyRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="48cea-128">Gets the property settings of the specified `mdAssemblyRef` token.</span><span class="sxs-lookup"><span data-stu-id="48cea-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="48cea-129">GetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="48cea-130">Gets the property settings of the specified COM type.</span><span class="sxs-lookup"><span data-stu-id="48cea-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="48cea-131">GetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="48cea-132">Gets the property settings of the specified file.</span><span class="sxs-lookup"><span data-stu-id="48cea-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="48cea-133">GetManifestResourceProps, méthode</span><span class="sxs-lookup"><span data-stu-id="48cea-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="48cea-134">Gets the property settings of the specified manifest resource.</span><span class="sxs-lookup"><span data-stu-id="48cea-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="48cea-135">spécifications</span><span class="sxs-lookup"><span data-stu-id="48cea-135">Requirements</span></span>  
 <span data-ttu-id="48cea-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48cea-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48cea-137">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="48cea-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="48cea-138">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="48cea-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="48cea-139">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48cea-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48cea-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48cea-140">See also</span></span>

- [<span data-ttu-id="48cea-141">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="48cea-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="48cea-142">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="48cea-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
