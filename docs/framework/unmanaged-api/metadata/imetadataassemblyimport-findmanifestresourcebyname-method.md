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
ms.openlocfilehash: ae9097725aecd21e910e49a78d81951df39e9b2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177775"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="de6ee-102">IMetaDataAssemblyImport::FindManifestResourceByName, méthode</span><span class="sxs-lookup"><span data-stu-id="de6ee-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="de6ee-103">Obtient un pointeur à la ressource manifeste avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="de6ee-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de6ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de6ee-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="de6ee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="de6ee-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="de6ee-106">[in] Nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="de6ee-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="de6ee-107">[out] Le tableau utilisé `mdManifestResource` pour stocker les jetons de métadonnées, dont chacun représente une ressource manifeste.</span><span class="sxs-lookup"><span data-stu-id="de6ee-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de6ee-108">Notes </span><span class="sxs-lookup"><span data-stu-id="de6ee-108">Remarks</span></span>  
 <span data-ttu-id="de6ee-109">La `FindManifestResourceByName` méthode utilise les règles standard employées par l’heure d’exécution de langue commune pour résoudre des références.</span><span class="sxs-lookup"><span data-stu-id="de6ee-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de6ee-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="de6ee-110">Requirements</span></span>  
 <span data-ttu-id="de6ee-111">**Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de6ee-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de6ee-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="de6ee-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de6ee-113">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="de6ee-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de6ee-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de6ee-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de6ee-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de6ee-115">See also</span></span>

- [<span data-ttu-id="de6ee-116">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="de6ee-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="de6ee-117">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="de6ee-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
