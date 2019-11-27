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
ms.openlocfilehash: 4faf8646b81f92ddf65eff15fdc610d275b37864
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440011"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="336dc-102">IMetaDataImport::EnumEvents, méthode</span><span class="sxs-lookup"><span data-stu-id="336dc-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="336dc-103">Énumère les jetons de définition d'événements pour le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="336dc-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="336dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="336dc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="336dc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="336dc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="336dc-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="336dc-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="336dc-107">dans Jeton TypeDef dont les définitions d’événements doivent être énumérées.</span><span class="sxs-lookup"><span data-stu-id="336dc-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="336dc-108">à Tableau d’événements retournés.</span><span class="sxs-lookup"><span data-stu-id="336dc-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="336dc-109">[in] Taille maximale du tableau `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="336dc-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="336dc-110">à Nombre réel d’événements retournés dans `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="336dc-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="336dc-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="336dc-111">Return Value</span></span>  
  
|<span data-ttu-id="336dc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="336dc-112">HRESULT</span></span>|<span data-ttu-id="336dc-113">Description</span><span class="sxs-lookup"><span data-stu-id="336dc-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="336dc-114">`EnumEvents` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="336dc-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="336dc-115">Il n’y a aucun événement à énumérer.</span><span class="sxs-lookup"><span data-stu-id="336dc-115">There are no events to enumerate.</span></span> <span data-ttu-id="336dc-116">Dans ce cas, `pcEvents` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="336dc-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="336dc-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="336dc-117">Requirements</span></span>  
 <span data-ttu-id="336dc-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="336dc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="336dc-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="336dc-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="336dc-120">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="336dc-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="336dc-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="336dc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="336dc-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="336dc-122">See also</span></span>

- [<span data-ttu-id="336dc-123">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="336dc-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="336dc-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="336dc-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
