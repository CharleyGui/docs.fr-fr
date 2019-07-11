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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85b0edc81a9a861a3eed6a7bc3ffc1ed1db37403
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770734"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="826e4-102">IMetaDataEmit::GetTokenFromTypeSpec, méthode</span><span class="sxs-lookup"><span data-stu-id="826e4-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="826e4-103">Obtient les métadonnées jeton pour le type avec la signature de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="826e4-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="826e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="826e4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="826e4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="826e4-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="826e4-106">[in] La signature qui est définie.</span><span class="sxs-lookup"><span data-stu-id="826e4-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="826e4-107">[in] Le nombre d’octets dans `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="826e4-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="826e4-108">[out] Le `mdTypeSpec` jeton attribué.</span><span class="sxs-lookup"><span data-stu-id="826e4-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="826e4-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="826e4-109">Requirements</span></span>  
 <span data-ttu-id="826e4-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="826e4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="826e4-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="826e4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="826e4-112">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="826e4-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="826e4-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="826e4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826e4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="826e4-114">See also</span></span>

- [<span data-ttu-id="826e4-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="826e4-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="826e4-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="826e4-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
