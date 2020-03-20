---
title: IMetaDataAssemblyImport::GetFileProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: dae4a36537eeac58ffb17ebc1b78d935ec807cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175978"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="05269-102">IMetaDataAssemblyImport::GetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="05269-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="05269-103">Obtient les propriétés du fichier avec la signature spécifiée de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="05269-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05269-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05269-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,
    [out] LPWSTR      szName,
    [in]  ULONG       cchName,
    [out] ULONG       *pchName,
    [out] const void  **ppbHashValue,
    [out] ULONG       *pcbHashValue,
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05269-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05269-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="05269-106">[dans] Le `mdFile` jeton de métadonnées qui représente le fichier pour lequel obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="05269-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="05269-107">[out] Le nom simple du fichier.</span><span class="sxs-lookup"><span data-stu-id="05269-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="05269-108">[dans] La taille, en chars `szName`larges, de .</span><span class="sxs-lookup"><span data-stu-id="05269-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="05269-109">[out] Le nombre de chars `szName`larges effectivement retourné dans .</span><span class="sxs-lookup"><span data-stu-id="05269-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="05269-110">[out] Un pointeur à la valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="05269-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="05269-111">C’est le hachage, en utilisant l’algorithme SHA-1, du fichier.</span><span class="sxs-lookup"><span data-stu-id="05269-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="05269-112">[out] Le nombre de chars larges dans la valeur de hachage retourné.</span><span class="sxs-lookup"><span data-stu-id="05269-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="05269-113">[out] Un pointeur pour les drapeaux qui décrivent les métadonnées appliquées à un fichier.</span><span class="sxs-lookup"><span data-stu-id="05269-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="05269-114">La valeur des drapeaux est une combinaison d’une ou plusieurs valeurs [CorFileFlags.](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="05269-114">The flags value is a combination of one or more [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05269-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="05269-115">Requirements</span></span>  
 <span data-ttu-id="05269-116">**Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05269-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05269-117">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="05269-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05269-118">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05269-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05269-119">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05269-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05269-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05269-120">See also</span></span>

- [<span data-ttu-id="05269-121">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="05269-121">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
