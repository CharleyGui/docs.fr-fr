---
title: IMetaDataAssemblyEmit::DefineManifestResource, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 5aa5d78faa8ca9261594e2a649b11088e1d78ee7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177867"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="3b075-102">IMetaDataAssemblyEmit::DefineManifestResource, méthode</span><span class="sxs-lookup"><span data-stu-id="3b075-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="3b075-103">Crée une structure `ManifestResource` contenant les métadonnées pour la ressource de manifeste spécifiée et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="3b075-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b075-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b075-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b075-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3b075-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="3b075-106">[in] Nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="3b075-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="3b075-107">[dans] Un jeton de métadonnées de type `mdtFile` ou `mdtAssemblyRef` qui cartes au fournisseur de ressources.</span><span class="sxs-lookup"><span data-stu-id="3b075-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="3b075-108">Une valeur NULL indique que le fichier dans lequel les métadonnées sont intégrées est le fournisseur de ressources.</span><span class="sxs-lookup"><span data-stu-id="3b075-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="3b075-109">[dans] La compensation au début de la ressource dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="3b075-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="3b075-110">Pour les ressources dans les fichiers autonomes, ce sera toujours zéro.</span><span class="sxs-lookup"><span data-stu-id="3b075-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="3b075-111">Si la ressource est intégrée dans un fichier PE (portable exécutable), il s’agit d’un décalage de la ressource BLOB, qui commence à l’emplacement spécifié dans le fichier d’en-tête cor.h.</span><span class="sxs-lookup"><span data-stu-id="3b075-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="3b075-112">[dans] Une combinaison peu sage de valeurs de drapeau qui spécifient les paramètres de propriété pour la définition de ressource.</span><span class="sxs-lookup"><span data-stu-id="3b075-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="3b075-113">[out] Un pointeur sur le jeton des métadonnées retournées.</span><span class="sxs-lookup"><span data-stu-id="3b075-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b075-114">Notes </span><span class="sxs-lookup"><span data-stu-id="3b075-114">Remarks</span></span>  
 <span data-ttu-id="3b075-115">Une `ManifestResource` structure de métadonnées doit être définie pour chaque ressource mise en œuvre dans chacun des dossiers de l’assemblée.</span><span class="sxs-lookup"><span data-stu-id="3b075-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b075-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3b075-116">Requirements</span></span>  
 <span data-ttu-id="3b075-117">**Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b075-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b075-118">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="3b075-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b075-119">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b075-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b075-120">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b075-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b075-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b075-121">See also</span></span>

- [<span data-ttu-id="3b075-122">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="3b075-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
