---
title: IMetaDataEmit2::SaveDeltaToMemory, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
ms.openlocfilehash: 5ec4fe2a8e949cf6e9aa0ce68f4d4e49b72170b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177436"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="ddb70-102">IMetaDataEmit2::SaveDeltaToMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="ddb70-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="ddb70-103">Enregistre les modifications de la session actuelle de modification et de poursuite à la mémoire.</span><span class="sxs-lookup"><span data-stu-id="ddb70-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddb70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddb70-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddb70-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ddb70-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="ddb70-106">[out] L’adresse à laquelle commencer à écrire le delta des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="ddb70-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="ddb70-107">[dans] La taille des changements.</span><span class="sxs-lookup"><span data-stu-id="ddb70-107">[in] The size of the changes.</span></span> <span data-ttu-id="ddb70-108">Utilisez [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) pour déterminer la taille.</span><span class="sxs-lookup"><span data-stu-id="ddb70-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddb70-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ddb70-109">Requirements</span></span>  
 <span data-ttu-id="ddb70-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddb70-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddb70-111">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="ddb70-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ddb70-112">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ddb70-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ddb70-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddb70-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddb70-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddb70-114">See also</span></span>

- [<span data-ttu-id="ddb70-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="ddb70-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="ddb70-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ddb70-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
