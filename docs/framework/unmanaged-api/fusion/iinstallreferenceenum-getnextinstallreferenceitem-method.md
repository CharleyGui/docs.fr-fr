---
title: IInstallReferenceEnum::GetNextInstallReferenceItem, méthode
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
ms.openlocfilehash: e093de7d2c2388274cbe9ebbe46084ee6ae3ff8c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721099"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="35a06-102">IInstallReferenceEnum::GetNextInstallReferenceItem, méthode</span><span class="sxs-lookup"><span data-stu-id="35a06-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>

<span data-ttu-id="35a06-103">Obtient un pointeur vers l’objet [IInstallReferenceItem](iinstallreferenceitem-interface.md) suivant contenu dans cet objet [IInstallReferenceEnum](iinstallreferenceenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="35a06-103">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35a06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35a06-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35a06-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="35a06-105">Parameters</span></span>  

 `ppRefItem`  
 <span data-ttu-id="35a06-106">à Pointeur retourné `IInstallReferenceItem` .</span><span class="sxs-lookup"><span data-stu-id="35a06-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="35a06-107">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="35a06-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="35a06-108">`dwFlags` doit avoir la valeur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="35a06-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="35a06-109">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="35a06-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="35a06-110">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="35a06-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35a06-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="35a06-111">Requirements</span></span>  

 <span data-ttu-id="35a06-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35a06-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35a06-113">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="35a06-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="35a06-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35a06-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a06-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35a06-115">See also</span></span>

- [<span data-ttu-id="35a06-116">IInstallReferenceItem, interface</span><span class="sxs-lookup"><span data-stu-id="35a06-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="35a06-117">IInstallReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="35a06-117">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
