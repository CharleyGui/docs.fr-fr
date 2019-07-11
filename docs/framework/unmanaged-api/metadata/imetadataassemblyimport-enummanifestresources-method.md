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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 717682bdcb2409a5f58f040a3ac2eafd73f01f7e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777955"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="0a597-102">IMetaDataAssemblyImport::EnumManifestResources, méthode</span><span class="sxs-lookup"><span data-stu-id="0a597-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="0a597-103">Obtient un pointeur vers un énumérateur pour les ressources référencées dans le manifeste d’assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="0a597-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a597-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a597-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="0a597-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0a597-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0a597-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="0a597-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="0a597-107">Cela doit être une valeur null valeur lorsque le `EnumManifestResources` méthode est appelée pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="0a597-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="0a597-108">[out] Tableau utilisé pour stocker le `mdManifestResource` des jetons de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="0a597-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0a597-109">[in] Le nombre maximal de `mdManifestResource` jetons qui peuvent être placés dans `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="0a597-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0a597-110">[out] Le nombre de `mdManifestResource` jetons placés dans `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="0a597-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a597-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0a597-111">Return Value</span></span>  
  
|<span data-ttu-id="0a597-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a597-112">HRESULT</span></span>|<span data-ttu-id="0a597-113">Description</span><span class="sxs-lookup"><span data-stu-id="0a597-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0a597-114">`EnumManifestResources` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="0a597-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0a597-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="0a597-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="0a597-116">Dans ce cas, `pcTokens` est défini à zéro.</span><span class="sxs-lookup"><span data-stu-id="0a597-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a597-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0a597-117">Requirements</span></span>  
 <span data-ttu-id="0a597-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a597-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a597-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0a597-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0a597-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a597-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0a597-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a597-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a597-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a597-122">See also</span></span>

- [<span data-ttu-id="0a597-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="0a597-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
