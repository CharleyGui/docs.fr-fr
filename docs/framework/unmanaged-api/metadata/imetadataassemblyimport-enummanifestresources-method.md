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
ms.openlocfilehash: 22141cf46a965c0624c076bd1d86d2624e5a09f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176017"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="cbd70-102">IMetaDataAssemblyImport::EnumManifestResources, méthode</span><span class="sxs-lookup"><span data-stu-id="cbd70-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="cbd70-103">Obtient un pointeur à un enumérateur pour les ressources référencées dans le manifeste d’assemblage actuel.</span><span class="sxs-lookup"><span data-stu-id="cbd70-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbd70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbd70-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="cbd70-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cbd70-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="cbd70-106">[dans, dehors] Un pointeur à l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="cbd70-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="cbd70-107">Cela doit être une `EnumManifestResources` valeur nulle lorsque la méthode est appelée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="cbd70-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="cbd70-108">[out] Le tableau utilisé `mdManifestResource` pour stocker les jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="cbd70-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cbd70-109">[dans] Le nombre `mdManifestResource` maximum de jetons qui `rManifestResources`peuvent être placés en .</span><span class="sxs-lookup"><span data-stu-id="cbd70-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="cbd70-110">[out] Le nombre `mdManifestResource` de jetons `rManifestResources`effectivement placés en .</span><span class="sxs-lookup"><span data-stu-id="cbd70-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbd70-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cbd70-111">Return Value</span></span>  
  
|<span data-ttu-id="cbd70-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cbd70-112">HRESULT</span></span>|<span data-ttu-id="cbd70-113">Description</span><span class="sxs-lookup"><span data-stu-id="cbd70-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cbd70-114">`EnumManifestResources`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="cbd70-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cbd70-115">Il n’y a pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="cbd70-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="cbd70-116">Dans ce `pcTokens` cas, est réglé à zéro.</span><span class="sxs-lookup"><span data-stu-id="cbd70-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cbd70-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cbd70-117">Requirements</span></span>  
 <span data-ttu-id="cbd70-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbd70-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbd70-119">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="cbd70-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cbd70-120">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cbd70-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cbd70-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbd70-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbd70-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbd70-122">See also</span></span>

- [<span data-ttu-id="cbd70-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="cbd70-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
