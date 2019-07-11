---
title: IInstallReferenceItem::GetReference, méthode
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b01c7cea477182c7590664ae9e850e99a89c4bc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773943"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="b1fd9-102">IInstallReferenceItem::GetReference, méthode</span><span class="sxs-lookup"><span data-stu-id="b1fd9-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="b1fd9-103">Obtient un pointeur vers le [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure représentée par ce [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="b1fd9-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1fd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1fd9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1fd9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b1fd9-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="b1fd9-106">[out] Retourné `FUSION_INSTALL_REFERENCE` pointeur.</span><span class="sxs-lookup"><span data-stu-id="b1fd9-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b1fd9-107">[in] Réservé pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="b1fd9-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="b1fd9-108">`dwFlags` doit être 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="b1fd9-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="b1fd9-109">[in] Réservé pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="b1fd9-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="b1fd9-110">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="b1fd9-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1fd9-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b1fd9-111">Requirements</span></span>  
 <span data-ttu-id="b1fd9-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1fd9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1fd9-113">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b1fd9-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b1fd9-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1fd9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1fd9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1fd9-115">See also</span></span>

- [<span data-ttu-id="b1fd9-116">IInstallReferenceItem, interface</span><span class="sxs-lookup"><span data-stu-id="b1fd9-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="b1fd9-117">FUSION_INSTALL_REFERENCE, structure</span><span class="sxs-lookup"><span data-stu-id="b1fd9-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
