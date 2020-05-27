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
ms.openlocfilehash: 944941c2356cae93ecc85f1714b4b29aefcb50ad
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008402"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="c143b-102">IMetaDataAssemblyImport::GetExportedTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="c143b-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="c143b-103">Obtient le jeu de propriétés du type exporté avec la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c143b-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c143b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c143b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c143b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c143b-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="c143b-106">dans `mdExportedType`Jeton de métadonnées qui représente le type exporté.</span><span class="sxs-lookup"><span data-stu-id="c143b-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="c143b-107">à Nom du type exporté.</span><span class="sxs-lookup"><span data-stu-id="c143b-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c143b-108">dans Taille, en caractères larges, de `szName` .</span><span class="sxs-lookup"><span data-stu-id="c143b-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="c143b-109">à Nombre de caractères larges réellement retournés dans`szName`</span><span class="sxs-lookup"><span data-stu-id="c143b-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="c143b-110">à Un `mdFile` `mdAssemblyRef` jeton de métadonnées,, ou `mdExportedType` qui contient ou autorise l’accès aux propriétés du type exporté.</span><span class="sxs-lookup"><span data-stu-id="c143b-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="c143b-111">à Pointeur vers un `mdTypeDef` jeton qui représente un type dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="c143b-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="c143b-112">à Pointeur vers les indicateurs qui décrivent les métadonnées appliquées au type exporté.</span><span class="sxs-lookup"><span data-stu-id="c143b-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="c143b-113">La valeur flags peut être une ou plusieurs valeurs [CorTypeAttr](cortypeattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="c143b-113">The flags value can be one or more [CorTypeAttr](cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c143b-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c143b-114">Requirements</span></span>  
 <span data-ttu-id="c143b-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c143b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c143b-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c143b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c143b-117">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c143b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c143b-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c143b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c143b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c143b-119">See also</span></span>

- [<span data-ttu-id="c143b-120">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="c143b-120">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
