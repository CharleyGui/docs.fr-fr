---
title: IMetaDataAssemblyImport::GetManifestResourceProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: d87d0d46ede65cf44c84edba92fe246174088a4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177664"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="2e10c-102">IMetaDataAssemblyImport::GetManifestResourceProps, méthode</span><span class="sxs-lookup"><span data-stu-id="2e10c-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="2e10c-103">Obtient l’ensemble des propriétés de la ressource manifeste avec la signature spécifiée de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="2e10c-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e10c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e10c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e10c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e10c-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="2e10c-106">[dans] Un `mdManifestResource` jeton qui représente la ressource pour laquelle obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="2e10c-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="2e10c-107">[out] Le nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="2e10c-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2e10c-108">[dans] La taille, en chars `szName`larges, de .</span><span class="sxs-lookup"><span data-stu-id="2e10c-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="2e10c-109">[out] Un pointeur sur le nombre de `szName`chars larges effectivement retourné dans .</span><span class="sxs-lookup"><span data-stu-id="2e10c-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="2e10c-110">[out] Un pointeur `mdFile` à un `mdAssemblyRef` jeton ou un jeton qui représente le fichier ou l’assemblage, respectivement, qui contient la ressource.</span><span class="sxs-lookup"><span data-stu-id="2e10c-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="2e10c-111">[out] Un pointeur à une valeur qui spécifie le décalage au début de la ressource dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="2e10c-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="2e10c-112">[out] Un pointeur pour les drapeaux qui décrivent les métadonnées appliquées à une ressource.</span><span class="sxs-lookup"><span data-stu-id="2e10c-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="2e10c-113">La valeur des drapeaux est une combinaison d’une ou plusieurs valeurs [CorManifestResourceFlags.](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="2e10c-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e10c-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2e10c-114">Requirements</span></span>  
 <span data-ttu-id="2e10c-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e10c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e10c-116">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="2e10c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e10c-117">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e10c-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e10c-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e10c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e10c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e10c-119">See also</span></span>

- [<span data-ttu-id="2e10c-120">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="2e10c-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
