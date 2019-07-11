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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 02331bb3b0c70b946eaa28c9cd316f109ac927b6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777240"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="b3627-102">IMetaDataEmit::SetRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="b3627-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="b3627-103">Définit l’adresse virtuelle relative de la méthode spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b3627-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3627-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3627-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3627-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b3627-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="b3627-106">[in] Le jeton pour la méthode cible ou l’implémentation de méthode.</span><span class="sxs-lookup"><span data-stu-id="b3627-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="b3627-107">[in] L’adresse de la zone de code ou de données.</span><span class="sxs-lookup"><span data-stu-id="b3627-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3627-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b3627-108">Requirements</span></span>  
 <span data-ttu-id="b3627-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3627-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3627-110">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b3627-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3627-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b3627-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3627-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3627-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3627-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3627-113">See also</span></span>

- [<span data-ttu-id="b3627-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="b3627-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b3627-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="b3627-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
