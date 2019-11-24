---
title: IMetaDataAssemblyEmit, interface
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
ms.openlocfilehash: 6b36d63101c1e9550a979d858764e9052cf45792
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447935"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="80d40-102">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="80d40-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="80d40-103">Fournit des méthodes qui prennent en charge le modèle d'autodescription utilisé par le Common Language Runtime pour résoudre et consommer des ressources.</span><span class="sxs-lookup"><span data-stu-id="80d40-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="80d40-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="80d40-104">Methods</span></span>  
  
|<span data-ttu-id="80d40-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="80d40-105">Method</span></span>|<span data-ttu-id="80d40-106">Description</span><span class="sxs-lookup"><span data-stu-id="80d40-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="80d40-107">DefineAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="80d40-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="80d40-108">Crée une structure de données d'assembly contenant les métadonnées pour l'assembly spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="80d40-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="80d40-109">DefineAssemblyRef, méthode</span><span class="sxs-lookup"><span data-stu-id="80d40-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="80d40-110">Crée une structure `AssemblyRef` contenant les métadonnées pour l'assembly que cet assembly référence et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="80d40-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="80d40-111">DefineExportedType, méthode</span><span class="sxs-lookup"><span data-stu-id="80d40-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="80d40-112">Crée une structure `ExportedType` contenant les métadonnées pour le type exporté spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="80d40-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="80d40-113">DefineFile, méthode</span><span class="sxs-lookup"><span data-stu-id="80d40-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="80d40-114">Crée une structure `File` contenant les métadonnées pour l'assembly référencé par cet assembly et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="80d40-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="80d40-115">DefineManifestResource, méthode</span><span class="sxs-lookup"><span data-stu-id="80d40-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="80d40-116">Crée une structure `ManifestResource` contenant les métadonnées pour la ressource de manifeste spécifiée et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="80d40-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="80d40-117">SetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="80d40-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="80d40-118">Modifie la structure de métadonnées `Assembly` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="80d40-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="80d40-119">SetAssemblyRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="80d40-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="80d40-120">Modifie la structure de métadonnées `AssemblyRef` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="80d40-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="80d40-121">SetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="80d40-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="80d40-122">Modifie la structure de métadonnées `ExportedType` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="80d40-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="80d40-123">SetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="80d40-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="80d40-124">Modifie la structure de métadonnées `File` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="80d40-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="80d40-125">SetManifestResourceProps, méthode</span><span class="sxs-lookup"><span data-stu-id="80d40-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="80d40-126">Modifie la structure de métadonnées `ManifestResource` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="80d40-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80d40-127">Notes</span><span class="sxs-lookup"><span data-stu-id="80d40-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80d40-128">spécifications</span><span class="sxs-lookup"><span data-stu-id="80d40-128">Requirements</span></span>  
 <span data-ttu-id="80d40-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80d40-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80d40-130">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="80d40-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80d40-131">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80d40-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80d40-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80d40-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d40-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80d40-133">See also</span></span>

- [<span data-ttu-id="80d40-134">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="80d40-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="80d40-135">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="80d40-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
