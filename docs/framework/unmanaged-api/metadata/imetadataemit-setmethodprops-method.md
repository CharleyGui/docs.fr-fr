---
title: IMetaDataEmit::SetMethodProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
ms.openlocfilehash: 9662a14b4ea97aed16968083489324d46c38dda2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177512"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="4f307-102">IMetaDataEmit::SetMethodProps, méthode</span><span class="sxs-lookup"><span data-stu-id="4f307-102">IMetaDataEmit::SetMethodProps Method</span></span>
<span data-ttu-id="4f307-103">Définit ou met à jour la fonctionnalité, stockée à l’adresse virtuelle relative spécifiée, d’une méthode définie par un appel antérieur à [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="4f307-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f307-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f307-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f307-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4f307-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="4f307-106">[dans] Le jeton pour la méthode à changer.</span><span class="sxs-lookup"><span data-stu-id="4f307-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="4f307-107">[dans] Le membre attribue.</span><span class="sxs-lookup"><span data-stu-id="4f307-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="4f307-108">[dans] L’adresse du code.</span><span class="sxs-lookup"><span data-stu-id="4f307-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="4f307-109">[dans] Les indicateurs de mise en œuvre de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4f307-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f307-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4f307-110">Requirements</span></span>  
 <span data-ttu-id="4f307-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f307-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f307-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="4f307-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f307-113">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4f307-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f307-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f307-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f307-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f307-115">See also</span></span>

- [<span data-ttu-id="4f307-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="4f307-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4f307-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="4f307-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
