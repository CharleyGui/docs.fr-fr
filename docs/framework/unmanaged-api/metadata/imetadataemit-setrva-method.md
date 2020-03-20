---
title: IMetaDataEmit::SetRVA, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type:
- apiref
ms.openlocfilehash: fe0b4b7fef0d05c4acc06dad5bc8a4eaf0722c9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175575"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="b7058-102">IMetaDataEmit::SetRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="b7058-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="b7058-103">Définit l’adresse virtuelle relative de la méthode spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b7058-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7058-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7058-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7058-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b7058-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="b7058-106">[dans] Le jeton pour la méthode cible ou la mise en œuvre de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b7058-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="b7058-107">[dans] L’adresse du code ou de la zone de données.</span><span class="sxs-lookup"><span data-stu-id="b7058-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7058-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b7058-108">Requirements</span></span>  
 <span data-ttu-id="b7058-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7058-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7058-110">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="b7058-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7058-111">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7058-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7058-112">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7058-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7058-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7058-113">See also</span></span>

- [<span data-ttu-id="b7058-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="b7058-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b7058-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="b7058-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
