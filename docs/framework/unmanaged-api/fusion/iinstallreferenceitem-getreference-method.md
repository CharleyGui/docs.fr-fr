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
ms.openlocfilehash: 9395fcc6d896114c25770edbc17761323285099f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796392"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="ee177-102">IInstallReferenceItem::GetReference, méthode</span><span class="sxs-lookup"><span data-stu-id="ee177-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="ee177-103">Obtient un pointeur vers la structure [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) représentée par cet objet [IInstallReferenceItem](iinstallreferenceitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ee177-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee177-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee177-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee177-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee177-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="ee177-106">à Pointeur retourné `FUSION_INSTALL_REFERENCE` .</span><span class="sxs-lookup"><span data-stu-id="ee177-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ee177-107">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="ee177-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ee177-108">`dwFlags`doit avoir la valeur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="ee177-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="ee177-109">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="ee177-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ee177-110">`pvReserved`doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="ee177-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee177-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ee177-111">Requirements</span></span>  
 <span data-ttu-id="ee177-112">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee177-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee177-113">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ee177-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ee177-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee177-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee177-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee177-115">See also</span></span>

- [<span data-ttu-id="ee177-116">IInstallReferenceItem, interface</span><span class="sxs-lookup"><span data-stu-id="ee177-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="ee177-117">FUSION_INSTALL_REFERENCE, structure</span><span class="sxs-lookup"><span data-stu-id="ee177-117">FUSION_INSTALL_REFERENCE Structure</span></span>](fusion-install-reference-structure.md)
