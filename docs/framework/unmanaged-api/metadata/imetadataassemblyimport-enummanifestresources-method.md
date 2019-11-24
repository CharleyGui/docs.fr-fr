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
ms.openlocfilehash: 2748460826deb422a3851713db11343209fe449a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449554"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="6843d-102">IMetaDataAssemblyImport::EnumManifestResources, méthode</span><span class="sxs-lookup"><span data-stu-id="6843d-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="6843d-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="6843d-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6843d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6843d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="6843d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6843d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6843d-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="6843d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6843d-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span><span class="sxs-lookup"><span data-stu-id="6843d-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="6843d-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span><span class="sxs-lookup"><span data-stu-id="6843d-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6843d-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="6843d-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="6843d-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="6843d-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6843d-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6843d-111">Return Value</span></span>  
  
|<span data-ttu-id="6843d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6843d-112">HRESULT</span></span>|<span data-ttu-id="6843d-113">Description</span><span class="sxs-lookup"><span data-stu-id="6843d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6843d-114">`EnumManifestResources` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="6843d-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6843d-115">There are no tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="6843d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="6843d-116">In this case, `pcTokens` is set to zero.</span><span class="sxs-lookup"><span data-stu-id="6843d-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6843d-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="6843d-117">Requirements</span></span>  
 <span data-ttu-id="6843d-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6843d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6843d-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6843d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6843d-120">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6843d-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6843d-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6843d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6843d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6843d-122">See also</span></span>

- [<span data-ttu-id="6843d-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="6843d-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
