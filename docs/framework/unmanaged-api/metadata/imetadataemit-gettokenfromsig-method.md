---
title: IMetaDataEmit::GetTokenFromSig, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
ms.openlocfilehash: d02943f28435fc00aad8e319aa260a24cca5e307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177588"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="82881-102">IMetaDataEmit::GetTokenFromSig, méthode</span><span class="sxs-lookup"><span data-stu-id="82881-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="82881-103">Obtient un jeton pour la signature spécifiée de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="82881-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82881-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82881-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82881-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82881-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="82881-106">[dans] La signature à persister et à stocker.</span><span class="sxs-lookup"><span data-stu-id="82881-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="82881-107">[dans] Le compte d’octets dans `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="82881-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="82881-108">[out] Le `mdSignature` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="82881-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82881-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="82881-109">Requirements</span></span>  
 <span data-ttu-id="82881-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82881-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82881-111">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="82881-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82881-112">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82881-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82881-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82881-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82881-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82881-114">See also</span></span>

- [<span data-ttu-id="82881-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="82881-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="82881-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="82881-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
