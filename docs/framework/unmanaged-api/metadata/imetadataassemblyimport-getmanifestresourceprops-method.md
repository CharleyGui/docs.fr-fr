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
ms.openlocfilehash: c0b6d53ce3be3aed6a577bf6e38a281928499848
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009026"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="b5ac4-102">IMetaDataAssemblyImport::GetManifestResourceProps, méthode</span><span class="sxs-lookup"><span data-stu-id="b5ac4-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="b5ac4-103">Obtient le jeu de propriétés de la ressource de manifeste avec la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b5ac4-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5ac4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5ac4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b5ac4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b5ac4-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="b5ac4-106">dans `mdManifestResource`Jeton qui représente la ressource pour laquelle obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="b5ac4-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="b5ac4-107">à Nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="b5ac4-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b5ac4-108">dans Taille, en caractères larges, de `szName` .</span><span class="sxs-lookup"><span data-stu-id="b5ac4-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b5ac4-109">à Pointeur vers le nombre de caractères larges réellement retournés dans `szName` .</span><span class="sxs-lookup"><span data-stu-id="b5ac4-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="b5ac4-110">à Pointeur vers un `mdFile` jeton ou un `mdAssemblyRef` jeton qui représente le fichier ou l’assembly, respectivement, qui contient la ressource.</span><span class="sxs-lookup"><span data-stu-id="b5ac4-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="b5ac4-111">à Pointeur vers une valeur qui spécifie le décalage au début de la ressource dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="b5ac4-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="b5ac4-112">à Pointeur vers des indicateurs qui décrivent les métadonnées appliquées à une ressource.</span><span class="sxs-lookup"><span data-stu-id="b5ac4-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="b5ac4-113">La valeur flags est une combinaison d’une ou plusieurs valeurs [CorManifestResourceFlags,](cormanifestresourceflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="b5ac4-113">The flags value is a combination of one or more [CorManifestResourceFlags](cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5ac4-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b5ac4-114">Requirements</span></span>  
 <span data-ttu-id="b5ac4-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5ac4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5ac4-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b5ac4-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b5ac4-117">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b5ac4-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b5ac4-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5ac4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ac4-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5ac4-119">See also</span></span>

- [<span data-ttu-id="b5ac4-120">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="b5ac4-120">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
