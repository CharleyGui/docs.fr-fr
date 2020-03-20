---
title: IMetaDataEmit::SaveToMemory, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
ms.openlocfilehash: d8843b2b5f69696dc206e9b530e3062ff225e89e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177581"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="dcbc9-102">IMetaDataEmit::SaveToMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="dcbc9-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="dcbc9-103">Enregistre toutes les métadonnées dans la portée actuelle à la zone de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dcbc9-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcbc9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcbc9-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcbc9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dcbc9-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="dcbc9-106">[out] L’adresse à laquelle commencer à écrire des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="dcbc9-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="dcbc9-107">[dans] La taille, dans les octets, de la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="dcbc9-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcbc9-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dcbc9-108">Requirements</span></span>  
 <span data-ttu-id="dcbc9-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcbc9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcbc9-110">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="dcbc9-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dcbc9-111">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dcbc9-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcbc9-112">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcbc9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcbc9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcbc9-113">See also</span></span>

- [<span data-ttu-id="dcbc9-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="dcbc9-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="dcbc9-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="dcbc9-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
