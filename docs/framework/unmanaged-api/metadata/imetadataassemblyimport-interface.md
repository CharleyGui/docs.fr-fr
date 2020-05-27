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
ms.openlocfilehash: 2a67f50fa1042e8d3957a9a0394507f260a328c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009013"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="83d0b-102">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="83d0b-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="83d0b-103">Fournit des méthodes pour accéder au contenu d'un manifeste d'assembly et l'examiner.</span><span class="sxs-lookup"><span data-stu-id="83d0b-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="83d0b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="83d0b-104">Methods</span></span>  
  
|<span data-ttu-id="83d0b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-105">Method</span></span>|<span data-ttu-id="83d0b-106">Description</span><span class="sxs-lookup"><span data-stu-id="83d0b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="83d0b-107">CloseEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-107">CloseEnum Method</span></span>](imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="83d0b-108">Libère le handle de l’énumérateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="83d0b-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="83d0b-109">EnumAssemblyRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-109">EnumAssemblyRefs Method</span></span>](imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="83d0b-110">Obtient un pointeur d’interface vers un énumérateur qui contient les `mdAssemblyRef` jetons des assemblys référencés par l’assembly dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="83d0b-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="83d0b-111">EnumExportedTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-111">EnumExportedTypes Method</span></span>](imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="83d0b-112">Obtient un pointeur d’interface vers un énumérateur qui contient les `mdExportedType` jetons des types com référencés par l’assembly dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="83d0b-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="83d0b-113">EnumFiles, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-113">EnumFiles Method</span></span>](imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="83d0b-114">Obtient un pointeur d’interface vers un énumérateur qui contient les `mdFile` jetons des fichiers référencés par l’assembly dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="83d0b-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="83d0b-115">EnumManifestResources, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-115">EnumManifestResources Method</span></span>](imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="83d0b-116">Obtient un pointeur d’interface vers un énumérateur qui contient les `mdManifestResource` jetons des ressources référencées par l’assembly dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="83d0b-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="83d0b-117">FindAssembliesByName, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-117">FindAssembliesByName Method</span></span>](imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="83d0b-118">Obtient un tableau de `mdAssemblyRef` jetons pour les assemblys avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="83d0b-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="83d0b-119">FindExportedTypeByName, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-119">FindExportedTypeByName Method</span></span>](imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="83d0b-120">Obtient un `mdExportedType` jeton pour le type com avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="83d0b-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="83d0b-121">FindManifestResourceByName, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-121">FindManifestResourceByName Method</span></span>](imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="83d0b-122">Obtient un `mdManifestResource` jeton pour la ressource avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="83d0b-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="83d0b-123">GetAssemblyFromScope, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-123">GetAssemblyFromScope Method</span></span>](imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="83d0b-124">Obtient le jeton de l’assembly dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="83d0b-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="83d0b-125">GetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-125">GetAssemblyProps Method</span></span>](imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="83d0b-126">Obtient les paramètres de propriété de l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="83d0b-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="83d0b-127">GetAssemblyRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-127">GetAssemblyRefProps Method</span></span>](imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="83d0b-128">Obtient les paramètres de propriété du `mdAssemblyRef` jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="83d0b-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="83d0b-129">GetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-129">GetExportedTypeProps Method</span></span>](imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="83d0b-130">Obtient les paramètres de propriété du type COM spécifié.</span><span class="sxs-lookup"><span data-stu-id="83d0b-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="83d0b-131">GetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-131">GetFileProps Method</span></span>](imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="83d0b-132">Obtient les paramètres de propriété du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="83d0b-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="83d0b-133">GetManifestResourceProps, méthode</span><span class="sxs-lookup"><span data-stu-id="83d0b-133">GetManifestResourceProps Method</span></span>](imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="83d0b-134">Obtient les paramètres de propriété de la ressource de manifeste spécifiée.</span><span class="sxs-lookup"><span data-stu-id="83d0b-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83d0b-135">Spécifications</span><span class="sxs-lookup"><span data-stu-id="83d0b-135">Requirements</span></span>  
 <span data-ttu-id="83d0b-136">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83d0b-136">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83d0b-137">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="83d0b-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83d0b-138">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="83d0b-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83d0b-139">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83d0b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d0b-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83d0b-140">See also</span></span>

- [<span data-ttu-id="83d0b-141">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="83d0b-141">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="83d0b-142">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="83d0b-142">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
