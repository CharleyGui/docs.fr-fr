---
title: IMetaDataEmit::SetFieldRVA, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
ms.openlocfilehash: 7648a1b3d219ee5d2b1ddc6b26f7b65c9ac85105
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175640"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="f1b0d-102">IMetaDataEmit::SetFieldRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="f1b0d-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="f1b0d-103">Établit une valeur variable globale pour l’adresse virtuelle relative du champ référencée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="f1b0d-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1b0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1b0d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1b0d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f1b0d-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="f1b0d-106">[dans] Le jeton pour le champ cible.</span><span class="sxs-lookup"><span data-stu-id="f1b0d-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="f1b0d-107">[dans] L’adresse d’un code ou d’une zone de données.</span><span class="sxs-lookup"><span data-stu-id="f1b0d-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1b0d-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f1b0d-108">Requirements</span></span>  
 <span data-ttu-id="f1b0d-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1b0d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1b0d-110">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="f1b0d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1b0d-111">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1b0d-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1b0d-112">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1b0d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b0d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1b0d-113">See also</span></span>

- [<span data-ttu-id="f1b0d-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f1b0d-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f1b0d-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="f1b0d-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
