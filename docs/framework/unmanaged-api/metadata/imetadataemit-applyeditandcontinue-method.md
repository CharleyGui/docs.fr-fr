---
title: IMetaDataEmit::ApplyEditAndContinue, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
ms.openlocfilehash: f876187624d066b9e672fbf44a984d6d02a54c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175874"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="ca831-102">IMetaDataEmit::ApplyEditAndContinue, méthode</span><span class="sxs-lookup"><span data-stu-id="ca831-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="ca831-103">Mise à jour de la portée actuelle de l’assemblage avec les modifications apportées dans les métadonnées spécifiées.</span><span class="sxs-lookup"><span data-stu-id="ca831-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca831-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca831-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca831-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca831-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="ca831-106">\[dans\] Pointer à un objet [IUnknown](/cpp/atl/iunknown) qui représente les métadonnées delta à partir du fichier portable exécutable (PE).</span><span class="sxs-lookup"><span data-stu-id="ca831-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="ca831-107">Les métadonnées delta sont le bloc de métadonnées qui comprend les modifications qui ont été apportées à la copie des métadonnées réelles du module.</span><span class="sxs-lookup"><span data-stu-id="ca831-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca831-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ca831-108">Requirements</span></span>  
 <span data-ttu-id="ca831-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca831-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca831-110">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="ca831-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca831-111">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca831-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca831-112">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca831-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca831-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca831-113">See also</span></span>

- [<span data-ttu-id="ca831-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ca831-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ca831-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="ca831-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
