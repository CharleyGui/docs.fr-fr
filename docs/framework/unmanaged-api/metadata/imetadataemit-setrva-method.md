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
ms.openlocfilehash: 3059d30f3969b4e19cee5a8d7a34c606f3849c05
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008740"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="89f0d-102">IMetaDataEmit::SetRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="89f0d-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="89f0d-103">Définit l’adresse virtuelle relative de la méthode spécifiée.</span><span class="sxs-lookup"><span data-stu-id="89f0d-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89f0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89f0d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89f0d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89f0d-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="89f0d-106">dans Jeton pour l’implémentation de la méthode ou de la méthode cible.</span><span class="sxs-lookup"><span data-stu-id="89f0d-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="89f0d-107">dans Adresse du code ou de la zone de données.</span><span class="sxs-lookup"><span data-stu-id="89f0d-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89f0d-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="89f0d-108">Requirements</span></span>  
 <span data-ttu-id="89f0d-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89f0d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89f0d-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="89f0d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89f0d-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="89f0d-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89f0d-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89f0d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f0d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89f0d-113">See also</span></span>

- [<span data-ttu-id="89f0d-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="89f0d-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="89f0d-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="89f0d-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
