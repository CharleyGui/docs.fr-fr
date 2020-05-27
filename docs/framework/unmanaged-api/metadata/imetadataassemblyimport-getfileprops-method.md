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
ms.openlocfilehash: 78c192f10f629a0c1316ae7af7fc774819f4de8f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007479"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="4f5e1-102">IMetaDataAssemblyImport::GetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="4f5e1-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>
<span data-ttu-id="4f5e1-103">Obtient les propriétés du fichier avec la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4f5e1-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f5e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f5e1-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4f5e1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4f5e1-105">Parameters</span></span>  
 `mdf`  
 <span data-ttu-id="4f5e1-106">dans `mdFile`Jeton de métadonnées qui représente le fichier pour lequel obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="4f5e1-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="4f5e1-107">à Nom simple du fichier.</span><span class="sxs-lookup"><span data-stu-id="4f5e1-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="4f5e1-108">dans Taille, en caractères larges, de `szName` .</span><span class="sxs-lookup"><span data-stu-id="4f5e1-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="4f5e1-109">à Nombre de caractères larges réellement retournés dans `szName` .</span><span class="sxs-lookup"><span data-stu-id="4f5e1-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="4f5e1-110">à Pointeur vers la valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="4f5e1-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="4f5e1-111">Il s’agit du hachage, à l’aide de l’algorithme SHA-1, du fichier.</span><span class="sxs-lookup"><span data-stu-id="4f5e1-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="4f5e1-112">à Nombre de caractères larges dans la valeur de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="4f5e1-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="4f5e1-113">à Pointeur vers les indicateurs qui décrivent les métadonnées appliquées à un fichier.</span><span class="sxs-lookup"><span data-stu-id="4f5e1-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="4f5e1-114">La valeur flags est une combinaison d’une ou plusieurs valeurs [CorFileFlags,](corfileflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="4f5e1-114">The flags value is a combination of one or more [CorFileFlags](corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f5e1-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4f5e1-115">Requirements</span></span>  
 <span data-ttu-id="4f5e1-116">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f5e1-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f5e1-117">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4f5e1-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f5e1-118">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4f5e1-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f5e1-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f5e1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f5e1-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f5e1-120">See also</span></span>

- [<span data-ttu-id="4f5e1-121">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="4f5e1-121">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
