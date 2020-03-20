---
title: IMetaDataImport::EnumEvents, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: bd50d63b1f7080f510c29f90979b7b36242af1c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177368"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="c6f99-102">IMetaDataImport::EnumEvents, méthode</span><span class="sxs-lookup"><span data-stu-id="c6f99-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="c6f99-103">Énumère les jetons de définition d'événements pour le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="c6f99-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6f99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6f99-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6f99-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c6f99-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c6f99-106">[dans, dehors] Un pointeur à l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="c6f99-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="c6f99-107">[dans] Le jeton TypeDef dont les définitions d’événements doivent être énumérées.</span><span class="sxs-lookup"><span data-stu-id="c6f99-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="c6f99-108">[out] La gamme d’événements retournés.</span><span class="sxs-lookup"><span data-stu-id="c6f99-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c6f99-109">[in] Taille maximale du tableau `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="c6f99-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="c6f99-110">[out] Le nombre réel d’événements retournés dans `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="c6f99-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6f99-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c6f99-111">Return Value</span></span>  
  
|<span data-ttu-id="c6f99-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6f99-112">HRESULT</span></span>|<span data-ttu-id="c6f99-113">Description</span><span class="sxs-lookup"><span data-stu-id="c6f99-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c6f99-114">`EnumEvents`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c6f99-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c6f99-115">Il n’y a pas d’événements à énumérer.</span><span class="sxs-lookup"><span data-stu-id="c6f99-115">There are no events to enumerate.</span></span> <span data-ttu-id="c6f99-116">Dans ce `pcEvents` cas, c’est zéro.</span><span class="sxs-lookup"><span data-stu-id="c6f99-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6f99-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c6f99-117">Requirements</span></span>  
 <span data-ttu-id="c6f99-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6f99-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6f99-119">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="c6f99-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6f99-120">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6f99-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6f99-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6f99-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6f99-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6f99-122">See also</span></span>

- [<span data-ttu-id="c6f99-123">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="c6f99-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c6f99-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="c6f99-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
