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
ms.openlocfilehash: 53b1234a176cade5876d70da0cb4eadc18802c69
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492302"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="d7f01-102">IMetaDataImport::EnumEvents, méthode</span><span class="sxs-lookup"><span data-stu-id="d7f01-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="d7f01-103">Énumère les jetons de définition d'événements pour le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="d7f01-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7f01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7f01-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7f01-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d7f01-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d7f01-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="d7f01-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="d7f01-107">dans Jeton TypeDef dont les définitions d’événements doivent être énumérées.</span><span class="sxs-lookup"><span data-stu-id="d7f01-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="d7f01-108">à Tableau d’événements retournés.</span><span class="sxs-lookup"><span data-stu-id="d7f01-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d7f01-109">[in] Taille maximale du tableau `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="d7f01-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="d7f01-110">à Nombre réel d’événements retournés dans `rEvents` .</span><span class="sxs-lookup"><span data-stu-id="d7f01-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7f01-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="d7f01-111">Return Value</span></span>  
  
|<span data-ttu-id="d7f01-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7f01-112">HRESULT</span></span>|<span data-ttu-id="d7f01-113">Description</span><span class="sxs-lookup"><span data-stu-id="d7f01-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d7f01-114">`EnumEvents`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d7f01-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d7f01-115">Il n’y a aucun événement à énumérer.</span><span class="sxs-lookup"><span data-stu-id="d7f01-115">There are no events to enumerate.</span></span> <span data-ttu-id="d7f01-116">Dans ce cas, `pcEvents` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="d7f01-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7f01-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d7f01-117">Requirements</span></span>  
 <span data-ttu-id="d7f01-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7f01-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7f01-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d7f01-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d7f01-120">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d7f01-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d7f01-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7f01-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7f01-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7f01-122">See also</span></span>

- [<span data-ttu-id="d7f01-123">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="d7f01-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d7f01-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="d7f01-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
