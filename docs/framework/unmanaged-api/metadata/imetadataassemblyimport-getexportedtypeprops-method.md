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
ms.openlocfilehash: 32224431051b958a3f01ffeb15cdb6db1dae2657
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722100"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="06f53-102">IMetaDataAssemblyImport::GetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="06f53-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>

<span data-ttu-id="06f53-103">Obtient le jeu de propriétés du type exporté avec la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="06f53-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06f53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06f53-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="06f53-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="06f53-105">Parameters</span></span>  

 `mdct`  
 <span data-ttu-id="06f53-106">dans `mdExportedType` Jeton de métadonnées qui représente le type exporté.</span><span class="sxs-lookup"><span data-stu-id="06f53-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="06f53-107">à Nom du type exporté.</span><span class="sxs-lookup"><span data-stu-id="06f53-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="06f53-108">dans Taille, en caractères larges, de `szName` .</span><span class="sxs-lookup"><span data-stu-id="06f53-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="06f53-109">à Nombre de caractères larges réellement retournés dans `szName`</span><span class="sxs-lookup"><span data-stu-id="06f53-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="06f53-110">à Un `mdFile` `mdAssemblyRef` jeton de métadonnées,, ou `mdExportedType` qui contient ou autorise l’accès aux propriétés du type exporté.</span><span class="sxs-lookup"><span data-stu-id="06f53-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="06f53-111">à Pointeur vers un `mdTypeDef` jeton qui représente un type dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="06f53-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="06f53-112">à Pointeur vers les indicateurs qui décrivent les métadonnées appliquées au type exporté.</span><span class="sxs-lookup"><span data-stu-id="06f53-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="06f53-113">La valeur flags peut être une ou plusieurs valeurs [CorTypeAttr](cortypeattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="06f53-113">The flags value can be one or more [CorTypeAttr](cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06f53-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="06f53-114">Requirements</span></span>  

 <span data-ttu-id="06f53-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06f53-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06f53-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="06f53-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="06f53-117">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="06f53-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="06f53-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06f53-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f53-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06f53-119">See also</span></span>

- [<span data-ttu-id="06f53-120">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="06f53-120">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
