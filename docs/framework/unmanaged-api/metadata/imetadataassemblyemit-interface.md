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
ms.openlocfilehash: 807e1ee831a43a4ef1e7b0a269ee38131f24081e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008116"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="bf64b-102">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="bf64b-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="bf64b-103">Fournit des méthodes qui prennent en charge le modèle d'autodescription utilisé par le Common Language Runtime pour résoudre et consommer des ressources.</span><span class="sxs-lookup"><span data-stu-id="bf64b-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf64b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bf64b-104">Methods</span></span>  
  
|<span data-ttu-id="bf64b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="bf64b-105">Method</span></span>|<span data-ttu-id="bf64b-106">Description</span><span class="sxs-lookup"><span data-stu-id="bf64b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf64b-107">DefineAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="bf64b-107">DefineAssembly Method</span></span>](imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="bf64b-108">Crée une structure de données d'assembly contenant les métadonnées pour l'assembly spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="bf64b-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="bf64b-109">DefineAssemblyRef, méthode</span><span class="sxs-lookup"><span data-stu-id="bf64b-109">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="bf64b-110">Crée une structure `AssemblyRef` contenant les métadonnées pour l'assembly que cet assembly référence et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="bf64b-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="bf64b-111">DefineExportedType, méthode</span><span class="sxs-lookup"><span data-stu-id="bf64b-111">DefineExportedType Method</span></span>](imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="bf64b-112">Crée une structure `ExportedType` contenant les métadonnées pour le type exporté spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="bf64b-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="bf64b-113">DefineFile, méthode</span><span class="sxs-lookup"><span data-stu-id="bf64b-113">DefineFile Method</span></span>](imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="bf64b-114">Crée une structure `File` contenant les métadonnées pour l'assembly référencé par cet assembly et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="bf64b-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="bf64b-115">DefineManifestResource, méthode</span><span class="sxs-lookup"><span data-stu-id="bf64b-115">DefineManifestResource Method</span></span>](imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="bf64b-116">Crée une structure `ManifestResource` contenant les métadonnées pour la ressource de manifeste spécifiée et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="bf64b-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="bf64b-117">SetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="bf64b-117">SetAssemblyProps Method</span></span>](imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="bf64b-118">Modifie la structure de métadonnées `Assembly` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bf64b-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="bf64b-119">SetAssemblyRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="bf64b-119">SetAssemblyRefProps Method</span></span>](imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="bf64b-120">Modifie la structure de métadonnées `AssemblyRef` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bf64b-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="bf64b-121">SetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="bf64b-121">SetExportedTypeProps Method</span></span>](imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="bf64b-122">Modifie la structure de métadonnées `ExportedType` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bf64b-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="bf64b-123">SetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="bf64b-123">SetFileProps Method</span></span>](imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="bf64b-124">Modifie la structure de métadonnées `File` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bf64b-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="bf64b-125">SetManifestResourceProps, méthode</span><span class="sxs-lookup"><span data-stu-id="bf64b-125">SetManifestResourceProps Method</span></span>](imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="bf64b-126">Modifie la structure de métadonnées `ManifestResource` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bf64b-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf64b-127">Notes</span><span class="sxs-lookup"><span data-stu-id="bf64b-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf64b-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bf64b-128">Requirements</span></span>  
 <span data-ttu-id="bf64b-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf64b-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf64b-130">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bf64b-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf64b-131">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bf64b-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bf64b-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf64b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf64b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf64b-133">See also</span></span>

- [<span data-ttu-id="bf64b-134">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="bf64b-134">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="bf64b-135">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="bf64b-135">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
