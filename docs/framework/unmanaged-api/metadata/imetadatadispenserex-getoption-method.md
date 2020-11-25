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
ms.openlocfilehash: 0ceadf42ac49fd3fc89c78a6a26b2f529afeeaf0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700559"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="445bb-102">IMetaDataDispenserEx::GetOption, méthode</span><span class="sxs-lookup"><span data-stu-id="445bb-102">IMetaDataDispenserEx::GetOption Method</span></span>

<span data-ttu-id="445bb-103">Obtient la valeur de l’option spécifiée pour la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="445bb-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="445bb-104">L’option contrôle la manière dont les appels à la portée de métadonnées actuelle sont gérés.</span><span class="sxs-lookup"><span data-stu-id="445bb-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="445bb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="445bb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="445bb-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="445bb-106">Parameters</span></span>  

 `optionId`  
 <span data-ttu-id="445bb-107">dans Pointeur vers un GUID qui spécifie l’option à récupérer.</span><span class="sxs-lookup"><span data-stu-id="445bb-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="445bb-108">Consultez la section Notes pour obtenir la liste des GUID pris en charge.</span><span class="sxs-lookup"><span data-stu-id="445bb-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="445bb-109">à Valeur de l’option retournée.</span><span class="sxs-lookup"><span data-stu-id="445bb-109">[out] The value of the returned option.</span></span> <span data-ttu-id="445bb-110">Le type de cette valeur sera une variante du type de l’option spécifiée.</span><span class="sxs-lookup"><span data-stu-id="445bb-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="445bb-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="445bb-111">Remarks</span></span>  

 <span data-ttu-id="445bb-112">La liste suivante répertorie les GUID pris en charge pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="445bb-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="445bb-113">Pour obtenir des descriptions, consultez la méthode [IMetaDataDispenserEx :: SetOption](imetadatadispenserex-setoption-method.md) .</span><span class="sxs-lookup"><span data-stu-id="445bb-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="445bb-114">Si `optionId` n’est pas dans cette liste, cette méthode retourne HRESULT `E_INVALIDARG` , indiquant un paramètre incorrect.</span><span class="sxs-lookup"><span data-stu-id="445bb-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="445bb-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="445bb-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="445bb-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="445bb-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="445bb-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="445bb-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="445bb-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="445bb-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="445bb-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="445bb-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="445bb-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="445bb-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="445bb-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="445bb-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="445bb-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="445bb-122">Requirements</span></span>  

 <span data-ttu-id="445bb-123">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="445bb-123">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="445bb-124">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="445bb-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="445bb-125">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="445bb-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="445bb-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="445bb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="445bb-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="445bb-127">See also</span></span>

- [<span data-ttu-id="445bb-128">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="445bb-128">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="445bb-129">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="445bb-129">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
