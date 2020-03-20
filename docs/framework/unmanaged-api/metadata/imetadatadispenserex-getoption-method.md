---
title: IMetaDataDispenserEx::GetOption, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
ms.openlocfilehash: 816e2f2dc7d4d00f74f67720ee45d7b3483e57fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177720"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="f7fe6-102">IMetaDataDispenserEx::GetOption, méthode</span><span class="sxs-lookup"><span data-stu-id="f7fe6-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="f7fe6-103">Obtient la valeur de l’option spécifiée pour la portée actuelle des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="f7fe6-104">L’option contrôle la façon dont les appels à la portée actuelle des métadonnées sont traités.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7fe6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7fe6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7fe6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7fe6-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="f7fe6-107">[dans] Un pointeur à un GUID qui spécifie l’option à récupérer.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="f7fe6-108">Consultez la section Remarques pour une liste de GUIDs pris en charge.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="f7fe6-109">[out] La valeur de l’option retournée.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-109">[out] The value of the returned option.</span></span> <span data-ttu-id="f7fe6-110">Le type de cette valeur sera une variante du type de l’option spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7fe6-111">Notes </span><span class="sxs-lookup"><span data-stu-id="f7fe6-111">Remarks</span></span>  
 <span data-ttu-id="f7fe6-112">La liste suivante montre les GUIDs qui sont pris en charge pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="f7fe6-113">Pour les descriptions, voir la méthode [IMetaDataDispenserEx::SetOption.](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)</span><span class="sxs-lookup"><span data-stu-id="f7fe6-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="f7fe6-114">Si `optionId` ce n’est pas dans cette `E_INVALIDARG`liste, cette méthode renvoie HRESULT , indiquant un paramètre incorrect.</span><span class="sxs-lookup"><span data-stu-id="f7fe6-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="f7fe6-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="f7fe6-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="f7fe6-116">MetaDataRefToDefCheck (en)</span><span class="sxs-lookup"><span data-stu-id="f7fe6-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="f7fe6-117">MétaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="f7fe6-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="f7fe6-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="f7fe6-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="f7fe6-119">MetaDataErrorIfEmitOutOfOrder MetaDataErrorIfEmitOutOfOrder MetaDataErrorIfEmitOutOfOrder MetaD</span><span class="sxs-lookup"><span data-stu-id="f7fe6-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="f7fe6-120">MétaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="f7fe6-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="f7fe6-121">MetaDataLinkerOptions MetaDataLinkerOptions MetaDataLinkerOptions MetaD</span><span class="sxs-lookup"><span data-stu-id="f7fe6-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7fe6-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f7fe6-122">Requirements</span></span>  
 <span data-ttu-id="f7fe6-123">**Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7fe6-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7fe6-124">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="f7fe6-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7fe6-125">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7fe6-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7fe6-126">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7fe6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7fe6-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7fe6-127">See also</span></span>

- [<span data-ttu-id="f7fe6-128">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="f7fe6-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="f7fe6-129">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="f7fe6-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
