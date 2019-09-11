---
title: IMetaDataAssemblyImport::FindManifestResourceByName, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aaaae5bda88d1fbc9949a080c5765127fd112bde
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855955"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="849c7-102">IMetaDataAssemblyImport::FindManifestResourceByName, méthode</span><span class="sxs-lookup"><span data-stu-id="849c7-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="849c7-103">Obtient un pointeur vers la ressource de manifeste portant le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="849c7-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="849c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="849c7-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="849c7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="849c7-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="849c7-106">dans Nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="849c7-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="849c7-107">à Tableau utilisé pour stocker les `mdManifestResource` jetons de métadonnées, chacun représentant une ressource de manifeste.</span><span class="sxs-lookup"><span data-stu-id="849c7-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="849c7-108">Notes</span><span class="sxs-lookup"><span data-stu-id="849c7-108">Remarks</span></span>  
 <span data-ttu-id="849c7-109">La `FindManifestResourceByName` méthode utilise les règles standard utilisées par le Common Language Runtime pour résoudre les références.</span><span class="sxs-lookup"><span data-stu-id="849c7-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="849c7-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="849c7-110">Requirements</span></span>  
 <span data-ttu-id="849c7-111">**Multi** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="849c7-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="849c7-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="849c7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="849c7-113">**Bibliothèque** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="849c7-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="849c7-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="849c7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="849c7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="849c7-115">See also</span></span>

- [<span data-ttu-id="849c7-116">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="849c7-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="849c7-117">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="849c7-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
