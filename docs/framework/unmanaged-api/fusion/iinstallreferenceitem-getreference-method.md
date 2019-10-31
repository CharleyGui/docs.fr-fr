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
ms.openlocfilehash: 014bd4f2b12c84790065f76a67765aaf35e8b2d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131679"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="a4c9e-102">IInstallReferenceItem::GetReference, méthode</span><span class="sxs-lookup"><span data-stu-id="a4c9e-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="a4c9e-103">Obtient un pointeur vers la structure [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) représentée par cet objet [IInstallReferenceItem](iinstallreferenceitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a4c9e-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4c9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4c9e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4c9e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a4c9e-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="a4c9e-106">à Pointeur de `FUSION_INSTALL_REFERENCE` retourné.</span><span class="sxs-lookup"><span data-stu-id="a4c9e-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a4c9e-107">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="a4c9e-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a4c9e-108">`dwFlags` doit avoir la valeur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="a4c9e-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="a4c9e-109">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="a4c9e-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a4c9e-110">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="a4c9e-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4c9e-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="a4c9e-111">Requirements</span></span>  
 <span data-ttu-id="a4c9e-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4c9e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4c9e-113">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a4c9e-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a4c9e-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4c9e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4c9e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4c9e-115">See also</span></span>

- [<span data-ttu-id="a4c9e-116">IInstallReferenceItem, interface</span><span class="sxs-lookup"><span data-stu-id="a4c9e-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="a4c9e-117">FUSION_INSTALL_REFERENCE, structure</span><span class="sxs-lookup"><span data-stu-id="a4c9e-117">FUSION_INSTALL_REFERENCE Structure</span></span>](fusion-install-reference-structure.md)
