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
ms.openlocfilehash: 740dad54bc3a79ff546176abdc35487d89ed8f44
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009247"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="d8a3a-102">IMetaDataEmit::GetTokenFromSig, méthode</span><span class="sxs-lookup"><span data-stu-id="d8a3a-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="d8a3a-103">Obtient un jeton pour la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d8a3a-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8a3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8a3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8a3a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d8a3a-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="d8a3a-106">dans Signature à rendre persistante et stockée.</span><span class="sxs-lookup"><span data-stu-id="d8a3a-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="d8a3a-107">dans Nombre d’octets dans `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="d8a3a-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="d8a3a-108">à `mdSignature`Jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="d8a3a-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8a3a-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d8a3a-109">Requirements</span></span>  
 <span data-ttu-id="d8a3a-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8a3a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8a3a-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d8a3a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8a3a-112">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d8a3a-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8a3a-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8a3a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8a3a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8a3a-114">See also</span></span>

- [<span data-ttu-id="d8a3a-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="d8a3a-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d8a3a-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="d8a3a-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
