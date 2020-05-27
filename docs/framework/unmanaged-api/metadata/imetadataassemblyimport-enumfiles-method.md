---
title: IMetaDataAssemblyImport::EnumFiles, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
ms.openlocfilehash: ed8bafd67b5d55a5116111b7721fbdc31c52aca6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009093"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="cee72-102">IMetaDataAssemblyImport::EnumFiles, méthode</span><span class="sxs-lookup"><span data-stu-id="cee72-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="cee72-103">Énumère les fichiers référencés dans le manifeste de l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="cee72-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cee72-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cee72-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cee72-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cee72-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="cee72-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="cee72-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="cee72-107">Il doit s’agir d’une valeur null pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="cee72-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="cee72-108">à Tableau utilisé pour stocker les `mdFile` jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="cee72-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cee72-109">dans Nombre maximal de `mdFile` jetons qui peuvent être placés dans `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="cee72-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="cee72-110">à Nombre de `mdFile` jetons réellement placés dans `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="cee72-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cee72-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="cee72-111">Return Value</span></span>  
  
|<span data-ttu-id="cee72-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cee72-112">HRESULT</span></span>|<span data-ttu-id="cee72-113">Description</span><span class="sxs-lookup"><span data-stu-id="cee72-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cee72-114">`EnumFiles`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="cee72-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cee72-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="cee72-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="cee72-116">Dans ce cas, `pcTokens` a la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="cee72-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cee72-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cee72-117">Requirements</span></span>  
 <span data-ttu-id="cee72-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cee72-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cee72-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cee72-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cee72-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cee72-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cee72-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cee72-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cee72-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cee72-122">See also</span></span>

- [<span data-ttu-id="cee72-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="cee72-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
