---
title: IMetaDataEmit::SaveToStream, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 7db27670b72a5018a03d4614b69486f67bcef155
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175679"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="4bb52-102">IMetaDataEmit::SaveToStream, méthode</span><span class="sxs-lookup"><span data-stu-id="4bb52-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="4bb52-103">Enregistre toutes les métadonnées dans `IStream`la portée actuelle à la spécifiée .</span><span class="sxs-lookup"><span data-stu-id="4bb52-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bb52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bb52-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bb52-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4bb52-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="4bb52-106">[dans] Le flux bref à économiser à.</span><span class="sxs-lookup"><span data-stu-id="4bb52-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="4bb52-107">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="4bb52-107">[in] Reserved.</span></span> <span data-ttu-id="4bb52-108">Doit être zéro.</span><span class="sxs-lookup"><span data-stu-id="4bb52-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bb52-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4bb52-109">Requirements</span></span>  
 <span data-ttu-id="4bb52-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bb52-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bb52-111">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="4bb52-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4bb52-112">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4bb52-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bb52-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bb52-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bb52-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bb52-114">See also</span></span>

- [<span data-ttu-id="4bb52-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="4bb52-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4bb52-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="4bb52-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
