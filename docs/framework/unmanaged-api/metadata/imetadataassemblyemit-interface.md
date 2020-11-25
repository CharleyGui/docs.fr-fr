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
ms.openlocfilehash: 5d8bc54a94e1571ff8335c934407bbf235179ecc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728288"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="6f310-102">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="6f310-102">IMetaDataAssemblyEmit Interface</span></span>

<span data-ttu-id="6f310-103">Fournit des méthodes qui prennent en charge le modèle d'autodescription utilisé par le Common Language Runtime pour résoudre et consommer des ressources.</span><span class="sxs-lookup"><span data-stu-id="6f310-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f310-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6f310-104">Methods</span></span>  
  
|<span data-ttu-id="6f310-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="6f310-105">Method</span></span>|<span data-ttu-id="6f310-106">Description</span><span class="sxs-lookup"><span data-stu-id="6f310-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f310-107">DefineAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="6f310-107">DefineAssembly Method</span></span>](imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="6f310-108">Crée une structure de données d'assembly contenant les métadonnées pour l'assembly spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="6f310-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6f310-109">DefineAssemblyRef, méthode</span><span class="sxs-lookup"><span data-stu-id="6f310-109">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="6f310-110">Crée une structure `AssemblyRef` contenant les métadonnées pour l'assembly que cet assembly référence et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="6f310-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6f310-111">DefineExportedType, méthode</span><span class="sxs-lookup"><span data-stu-id="6f310-111">DefineExportedType Method</span></span>](imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="6f310-112">Crée une structure `ExportedType` contenant les métadonnées pour le type exporté spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="6f310-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6f310-113">DefineFile, méthode</span><span class="sxs-lookup"><span data-stu-id="6f310-113">DefineFile Method</span></span>](imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="6f310-114">Crée une structure `File` contenant les métadonnées pour l'assembly référencé par cet assembly et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="6f310-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6f310-115">DefineManifestResource, méthode</span><span class="sxs-lookup"><span data-stu-id="6f310-115">DefineManifestResource Method</span></span>](imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="6f310-116">Crée une structure `ManifestResource` contenant les métadonnées pour la ressource de manifeste spécifiée et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="6f310-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="6f310-117">SetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="6f310-117">SetAssemblyProps Method</span></span>](imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="6f310-118">Modifie la structure de métadonnées `Assembly` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6f310-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="6f310-119">SetAssemblyRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="6f310-119">SetAssemblyRefProps Method</span></span>](imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="6f310-120">Modifie la structure de métadonnées `AssemblyRef` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6f310-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="6f310-121">SetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="6f310-121">SetExportedTypeProps Method</span></span>](imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="6f310-122">Modifie la structure de métadonnées `ExportedType` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6f310-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="6f310-123">SetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="6f310-123">SetFileProps Method</span></span>](imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="6f310-124">Modifie la structure de métadonnées `File` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6f310-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="6f310-125">SetManifestResourceProps, méthode</span><span class="sxs-lookup"><span data-stu-id="6f310-125">SetManifestResourceProps Method</span></span>](imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="6f310-126">Modifie la structure de métadonnées `ManifestResource` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6f310-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f310-127">Notes</span><span class="sxs-lookup"><span data-stu-id="6f310-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f310-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6f310-128">Requirements</span></span>  

 <span data-ttu-id="6f310-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f310-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f310-130">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6f310-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f310-131">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f310-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f310-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f310-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f310-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f310-133">See also</span></span>

- [<span data-ttu-id="6f310-134">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="6f310-134">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="6f310-135">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="6f310-135">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
