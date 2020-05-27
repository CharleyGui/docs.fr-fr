---
title: IMetaDataEmit::Merge, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: e7fe5cbe27c0771a71e4c03d14ab68ada7d0741a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004164"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="11a46-102">IMetaDataEmit::Merge, méthode</span><span class="sxs-lookup"><span data-stu-id="11a46-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="11a46-103">Ajoute l’étendue importée spécifiée à la liste des étendues à fusionner.</span><span class="sxs-lookup"><span data-stu-id="11a46-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11a46-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11a46-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="11a46-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="11a46-106">dans Pointeur vers un objet [IMetaDataImport](imetadataimport-interface.md) qui identifie l’étendue importée à fusionner.</span><span class="sxs-lookup"><span data-stu-id="11a46-106">[in] A pointer to an [IMetaDataImport](imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="11a46-107">dans Pointeur vers un objet [IMapToken](imaptoken-interface.md) qui spécifie le nouveau mappage du jeton.</span><span class="sxs-lookup"><span data-stu-id="11a46-107">[in] A pointer to an [IMapToken](imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="11a46-108">dans Pointeur vers un objet [IUnknown](/cpp/atl/iunknown) qui spécifie les erreurs.</span><span class="sxs-lookup"><span data-stu-id="11a46-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11a46-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="11a46-109">Remarks</span></span>  
 <span data-ttu-id="11a46-110">Appelez [IMetaDataEmit :: MergeEnd,](imetadataemit-mergeend-method.md) pour déclencher la fusion des métadonnées dans une seule portée.</span><span class="sxs-lookup"><span data-stu-id="11a46-110">Call [IMetaDataEmit::MergeEnd](imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11a46-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="11a46-111">Requirements</span></span>  
 <span data-ttu-id="11a46-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11a46-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11a46-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="11a46-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11a46-114">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="11a46-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11a46-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11a46-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a46-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11a46-116">See also</span></span>

- [<span data-ttu-id="11a46-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="11a46-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="11a46-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="11a46-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
