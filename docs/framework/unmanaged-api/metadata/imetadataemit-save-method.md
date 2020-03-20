---
title: IMetaDataEmit::Save, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
ms.openlocfilehash: 76f18336808e6832b2ded94349efd7948f23a1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175692"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="3f531-102">IMetaDataEmit::Save, méthode</span><span class="sxs-lookup"><span data-stu-id="3f531-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="3f531-103">Enregistre toutes les métadonnées dans la portée actuelle du fichier à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="3f531-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f531-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f531-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (
    [in]  LPCWSTR     szFile,
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f531-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3f531-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="3f531-106">[dans] Le nom du fichier à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="3f531-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="3f531-107">Si cette valeur est nulle, la copie en mémoire sera enregistrée au dernier endroit qui a été utilisé.</span><span class="sxs-lookup"><span data-stu-id="3f531-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="3f531-108">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="3f531-108">[in] Reserved.</span></span> <span data-ttu-id="3f531-109">Doit être zéro.</span><span class="sxs-lookup"><span data-stu-id="3f531-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f531-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3f531-110">Requirements</span></span>  
 <span data-ttu-id="3f531-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f531-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f531-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="3f531-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f531-113">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f531-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f531-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f531-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f531-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f531-115">See also</span></span>

- [<span data-ttu-id="3f531-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="3f531-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3f531-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="3f531-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
