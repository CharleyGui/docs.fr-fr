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
ms.openlocfilehash: 0b9ff2716cc0bc32c81fe6fcdd4e6c367d4d835f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718174"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a><span data-ttu-id="b45aa-102">IMetaDataAssemblyImport::GetFileProps, méthode</span><span class="sxs-lookup"><span data-stu-id="b45aa-102">IMetaDataAssemblyImport::GetFileProps Method</span></span>

<span data-ttu-id="b45aa-103">Obtient les propriétés du fichier avec la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b45aa-103">Gets the properties of the file with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b45aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b45aa-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b45aa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b45aa-105">Parameters</span></span>  

 `mdf`  
 <span data-ttu-id="b45aa-106">dans `mdFile` Jeton de métadonnées qui représente le fichier pour lequel obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="b45aa-106">[in] The `mdFile` metadata token that represents the file for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="b45aa-107">à Nom simple du fichier.</span><span class="sxs-lookup"><span data-stu-id="b45aa-107">[out] The simple name of the file.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b45aa-108">dans Taille, en caractères larges, de `szName` .</span><span class="sxs-lookup"><span data-stu-id="b45aa-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b45aa-109">à Nombre de caractères larges réellement retournés dans `szName` .</span><span class="sxs-lookup"><span data-stu-id="b45aa-109">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="b45aa-110">à Pointeur vers la valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="b45aa-110">[out] A pointer to the hash value.</span></span> <span data-ttu-id="b45aa-111">Il s’agit du hachage, à l’aide de l’algorithme SHA-1, du fichier.</span><span class="sxs-lookup"><span data-stu-id="b45aa-111">This is the hash, using the SHA-1 algorithm, of the file.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="b45aa-112">à Nombre de caractères larges dans la valeur de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="b45aa-112">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwFileFlags`  
 <span data-ttu-id="b45aa-113">à Pointeur vers les indicateurs qui décrivent les métadonnées appliquées à un fichier.</span><span class="sxs-lookup"><span data-stu-id="b45aa-113">[out] A pointer to the flags that describe the metadata applied to a file.</span></span> <span data-ttu-id="b45aa-114">La valeur flags est une combinaison d’une ou plusieurs valeurs [CorFileFlags,](corfileflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="b45aa-114">The flags value is a combination of one or more [CorFileFlags](corfileflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b45aa-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b45aa-115">Requirements</span></span>  

 <span data-ttu-id="b45aa-116">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b45aa-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b45aa-117">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b45aa-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b45aa-118">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b45aa-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b45aa-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b45aa-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45aa-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b45aa-120">See also</span></span>

- [<span data-ttu-id="b45aa-121">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="b45aa-121">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
