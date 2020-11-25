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
ms.openlocfilehash: 0cc84893c4937bf6b23eae0d63b92b3b871901dd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700572"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="a1909-102">IMetaDataEmit::ApplyEditAndContinue, méthode</span><span class="sxs-lookup"><span data-stu-id="a1909-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>

<span data-ttu-id="a1909-103">Met à jour la portée de l’assembly actuel avec les modifications apportées aux métadonnées spécifiées.</span><span class="sxs-lookup"><span data-stu-id="a1909-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1909-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1909-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1909-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1909-105">Parameters</span></span>  

 `pImport`  
 <span data-ttu-id="a1909-106">\[\]pointeur vers un objet [IUnknown](/cpp/atl/iunknown) qui représente les métadonnées Delta du fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="a1909-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="a1909-107">Les métadonnées Delta sont le bloc de métadonnées qui comprend les modifications apportées à la copie des métadonnées réelles du module.</span><span class="sxs-lookup"><span data-stu-id="a1909-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1909-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a1909-108">Requirements</span></span>  

 <span data-ttu-id="a1909-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1909-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1909-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a1909-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a1909-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1909-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1909-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1909-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1909-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1909-113">See also</span></span>

- [<span data-ttu-id="a1909-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="a1909-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a1909-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="a1909-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
