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
ms.openlocfilehash: f9af770f3bdca98f6b3d06d8b0fe6c92745f73e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731616"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="86d0a-102">IMetaDataAssemblyImport::EnumFiles, méthode</span><span class="sxs-lookup"><span data-stu-id="86d0a-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>

<span data-ttu-id="86d0a-103">Énumère les fichiers référencés dans le manifeste de l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="86d0a-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d0a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86d0a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,
    [out] mdFile          rFiles[],
    [in]  ULONG           cMax,
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86d0a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="86d0a-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="86d0a-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="86d0a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="86d0a-107">Il doit s’agir d’une valeur null pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="86d0a-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="86d0a-108">à Tableau utilisé pour stocker les `mdFile` jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="86d0a-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="86d0a-109">dans Nombre maximal de `mdFile` jetons qui peuvent être placés dans `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="86d0a-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="86d0a-110">à Nombre de `mdFile` jetons réellement placés dans `rFiles` .</span><span class="sxs-lookup"><span data-stu-id="86d0a-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86d0a-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="86d0a-111">Return Value</span></span>  
  
|<span data-ttu-id="86d0a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86d0a-112">HRESULT</span></span>|<span data-ttu-id="86d0a-113">Description</span><span class="sxs-lookup"><span data-stu-id="86d0a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="86d0a-114">`EnumFiles` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="86d0a-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="86d0a-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="86d0a-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="86d0a-116">Dans ce cas, `pcTokens` a la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="86d0a-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86d0a-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="86d0a-117">Requirements</span></span>  

 <span data-ttu-id="86d0a-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86d0a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86d0a-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="86d0a-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="86d0a-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="86d0a-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="86d0a-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86d0a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d0a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86d0a-122">See also</span></span>

- [<span data-ttu-id="86d0a-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="86d0a-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
