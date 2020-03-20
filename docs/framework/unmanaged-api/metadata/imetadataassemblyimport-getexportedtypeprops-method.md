---
title: IMetaDataAssemblyImport::GetExportedTypeProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
ms.openlocfilehash: 15b58e01d4ce99f19f510c760819471b84380b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177755"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="f5303-102">IMetaDataAssemblyImport::GetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="f5303-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="f5303-103">Obtient l’ensemble des propriétés du type exporté avec la signature spécifiée de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f5303-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5303-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5303-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,
    [out] LPWSTR            szName,
    [in]  ULONG             cchName,
    [out] ULONG             *pchName,
    [out] mdToken           *ptkImplementation,
    [out] mdTypeDef         *ptkTypeDef,
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5303-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f5303-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="f5303-106">[dans] Un `mdExportedType` jeton de métadonnées qui représente le type exporté.</span><span class="sxs-lookup"><span data-stu-id="f5303-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="f5303-107">[out] Le nom du type exporté.</span><span class="sxs-lookup"><span data-stu-id="f5303-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f5303-108">[dans] La taille, en caractères larges, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="f5303-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="f5303-109">[out] Le nombre de caractères larges effectivement retourné dans`szName`</span><span class="sxs-lookup"><span data-stu-id="f5303-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="f5303-110">[out] Un `mdFile` `mdAssemblyRef`jeton, ou `mdExportedType` des métadonnées qui contient ou permet l’accès aux propriétés du type exporté.</span><span class="sxs-lookup"><span data-stu-id="f5303-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="f5303-111">[out] Un pointeur `mdTypeDef` à un jeton qui représente un type dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="f5303-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="f5303-112">[out] Un pointeur vers les drapeaux qui décrivent les métadonnées appliquées au type exporté.</span><span class="sxs-lookup"><span data-stu-id="f5303-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="f5303-113">La valeur des drapeaux peut être une ou plusieurs valeurs [CorTypeAttr.](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="f5303-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5303-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f5303-114">Requirements</span></span>  
 <span data-ttu-id="f5303-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5303-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5303-116">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="f5303-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f5303-117">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5303-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f5303-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5303-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5303-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5303-119">See also</span></span>

- [<span data-ttu-id="f5303-120">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="f5303-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
