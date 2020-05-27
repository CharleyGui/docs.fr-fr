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
ms.openlocfilehash: 7ce9ac95c7183a7d47c367914d80f77c57dde0d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005763"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="f7e29-102">IMetaDataEmit::ApplyEditAndContinue, méthode</span><span class="sxs-lookup"><span data-stu-id="f7e29-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="f7e29-103">Met à jour la portée de l’assembly actuel avec les modifications apportées aux métadonnées spécifiées.</span><span class="sxs-lookup"><span data-stu-id="f7e29-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7e29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7e29-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7e29-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7e29-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="f7e29-106">\[\]pointeur vers un objet [IUnknown](/cpp/atl/iunknown) qui représente les métadonnées Delta du fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="f7e29-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="f7e29-107">Les métadonnées Delta sont le bloc de métadonnées qui comprend les modifications apportées à la copie des métadonnées réelles du module.</span><span class="sxs-lookup"><span data-stu-id="f7e29-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7e29-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f7e29-108">Requirements</span></span>  
 <span data-ttu-id="f7e29-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7e29-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7e29-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f7e29-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7e29-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f7e29-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7e29-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7e29-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e29-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7e29-113">See also</span></span>

- [<span data-ttu-id="f7e29-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f7e29-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f7e29-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="f7e29-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
