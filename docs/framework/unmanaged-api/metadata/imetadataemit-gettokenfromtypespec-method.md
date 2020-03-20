---
title: IMetaDataEmit::GetTokenFromTypeSpec, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
ms.openlocfilehash: 8c609d730297881c0ac20dca8569f0e9492638e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175718"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="19c80-102">IMetaDataEmit::GetTokenFromTypeSpec, méthode</span><span class="sxs-lookup"><span data-stu-id="19c80-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="19c80-103">Obtient un jeton de métadonnées pour le type avec la signature spécifiée de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="19c80-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19c80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19c80-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19c80-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="19c80-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="19c80-106">[dans] La signature étant définie.</span><span class="sxs-lookup"><span data-stu-id="19c80-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="19c80-107">[dans] Le compte d’octets dans `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="19c80-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="19c80-108">[out] Le `mdTypeSpec` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="19c80-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19c80-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="19c80-109">Requirements</span></span>  
 <span data-ttu-id="19c80-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19c80-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19c80-111">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="19c80-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19c80-112">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19c80-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19c80-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19c80-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19c80-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19c80-114">See also</span></span>

- [<span data-ttu-id="19c80-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="19c80-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="19c80-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="19c80-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
