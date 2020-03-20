---
title: IMetaDataEmit2::SaveDeltaToStream, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
ms.openlocfilehash: 7e8376f3a029b0e3ec51a1e7587dd14b3e7530ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177425"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="6720a-102">IMetaDataEmit2::SaveDeltaToStream, méthode</span><span class="sxs-lookup"><span data-stu-id="6720a-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="6720a-103">Enregistre les modifications de la session actuelle de modification et de poursuite au flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="6720a-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6720a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6720a-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6720a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6720a-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="6720a-106">[dans] Un pointeur d’interface pour le flux bref auquel enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="6720a-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="6720a-107">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="6720a-107">[in] Reserved.</span></span> <span data-ttu-id="6720a-108">Cette valeur doit être zéro.</span><span class="sxs-lookup"><span data-stu-id="6720a-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6720a-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6720a-109">Requirements</span></span>  
 <span data-ttu-id="6720a-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6720a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6720a-111">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="6720a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6720a-112">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6720a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6720a-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6720a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6720a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6720a-114">See also</span></span>

- [<span data-ttu-id="6720a-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="6720a-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="6720a-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="6720a-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
