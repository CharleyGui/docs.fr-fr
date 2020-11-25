---
title: IMetaDataAssemblyImport::EnumManifestResources, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
ms.openlocfilehash: c72e5b9544d1d8ae989405ac9bfdb22050b1aaaf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731606"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="0f8f8-102">IMetaDataAssemblyImport::EnumManifestResources, méthode</span><span class="sxs-lookup"><span data-stu-id="0f8f8-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>

<span data-ttu-id="0f8f8-103">Obtient un pointeur vers un énumérateur pour les ressources référencées dans le manifeste de l’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="0f8f8-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f8f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f8f8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="0f8f8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0f8f8-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="0f8f8-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="0f8f8-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="0f8f8-107">Il doit s’agir d’une valeur NULL lorsque la `EnumManifestResources` méthode est appelée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="0f8f8-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="0f8f8-108">à Tableau utilisé pour stocker les `mdManifestResource` jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="0f8f8-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0f8f8-109">dans Nombre maximal de `mdManifestResource` jetons qui peuvent être placés dans `rManifestResources` .</span><span class="sxs-lookup"><span data-stu-id="0f8f8-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0f8f8-110">à Nombre de `mdManifestResource` jetons réellement placés dans `rManifestResources` .</span><span class="sxs-lookup"><span data-stu-id="0f8f8-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f8f8-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="0f8f8-111">Return Value</span></span>  
  
|<span data-ttu-id="0f8f8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f8f8-112">HRESULT</span></span>|<span data-ttu-id="0f8f8-113">Description</span><span class="sxs-lookup"><span data-stu-id="0f8f8-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0f8f8-114">`EnumManifestResources` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="0f8f8-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0f8f8-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="0f8f8-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="0f8f8-116">Dans ce cas, `pcTokens` a la valeur zéro.</span><span class="sxs-lookup"><span data-stu-id="0f8f8-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f8f8-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0f8f8-117">Requirements</span></span>  

 <span data-ttu-id="0f8f8-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f8f8-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f8f8-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0f8f8-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f8f8-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f8f8-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f8f8-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f8f8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f8f8-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f8f8-122">See also</span></span>

- [<span data-ttu-id="0f8f8-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="0f8f8-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
