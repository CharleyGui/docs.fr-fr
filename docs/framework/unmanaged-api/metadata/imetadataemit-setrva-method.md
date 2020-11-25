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
ms.openlocfilehash: df9dc1a36a9adcef3f93a9929565cef117e84d75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704225"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="5eda6-102">IMetaDataEmit::SetRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="5eda6-102">IMetaDataEmit::SetRVA Method</span></span>

<span data-ttu-id="5eda6-103">Définit l’adresse virtuelle relative de la méthode spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5eda6-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eda6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5eda6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5eda6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5eda6-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="5eda6-106">dans Jeton pour l’implémentation de la méthode ou de la méthode cible.</span><span class="sxs-lookup"><span data-stu-id="5eda6-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="5eda6-107">dans Adresse du code ou de la zone de données.</span><span class="sxs-lookup"><span data-stu-id="5eda6-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5eda6-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5eda6-108">Requirements</span></span>  

 <span data-ttu-id="5eda6-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5eda6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5eda6-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5eda6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5eda6-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5eda6-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5eda6-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5eda6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eda6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5eda6-113">See also</span></span>

- [<span data-ttu-id="5eda6-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="5eda6-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5eda6-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="5eda6-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
