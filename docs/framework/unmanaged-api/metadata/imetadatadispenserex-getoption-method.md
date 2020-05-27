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
ms.openlocfilehash: 832adacac4a6df9ccf21578538a1c557150f3ba1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008779"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="510ea-102">IMetaDataDispenserEx::GetOption, méthode</span><span class="sxs-lookup"><span data-stu-id="510ea-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="510ea-103">Obtient la valeur de l’option spécifiée pour la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="510ea-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="510ea-104">L’option contrôle la manière dont les appels à la portée de métadonnées actuelle sont gérés.</span><span class="sxs-lookup"><span data-stu-id="510ea-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="510ea-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="510ea-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="510ea-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="510ea-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="510ea-107">dans Pointeur vers un GUID qui spécifie l’option à récupérer.</span><span class="sxs-lookup"><span data-stu-id="510ea-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="510ea-108">Consultez la section Notes pour obtenir la liste des GUID pris en charge.</span><span class="sxs-lookup"><span data-stu-id="510ea-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="510ea-109">à Valeur de l’option retournée.</span><span class="sxs-lookup"><span data-stu-id="510ea-109">[out] The value of the returned option.</span></span> <span data-ttu-id="510ea-110">Le type de cette valeur sera une variante du type de l’option spécifiée.</span><span class="sxs-lookup"><span data-stu-id="510ea-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="510ea-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="510ea-111">Remarks</span></span>  
 <span data-ttu-id="510ea-112">La liste suivante répertorie les GUID pris en charge pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="510ea-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="510ea-113">Pour obtenir des descriptions, consultez la méthode [IMetaDataDispenserEx :: SetOption](imetadatadispenserex-setoption-method.md) .</span><span class="sxs-lookup"><span data-stu-id="510ea-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="510ea-114">Si `optionId` n’est pas dans cette liste, cette méthode retourne HRESULT `E_INVALIDARG` , indiquant un paramètre incorrect.</span><span class="sxs-lookup"><span data-stu-id="510ea-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="510ea-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="510ea-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="510ea-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="510ea-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="510ea-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="510ea-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="510ea-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="510ea-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="510ea-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="510ea-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="510ea-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="510ea-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="510ea-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="510ea-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="510ea-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="510ea-122">Requirements</span></span>  
 <span data-ttu-id="510ea-123">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="510ea-123">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="510ea-124">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="510ea-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="510ea-125">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="510ea-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="510ea-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="510ea-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="510ea-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="510ea-127">See also</span></span>

- [<span data-ttu-id="510ea-128">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="510ea-128">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="510ea-129">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="510ea-129">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
