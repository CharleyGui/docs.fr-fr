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
ms.openlocfilehash: 0dad50f1acac38f8cdc505026e88d42882deb580
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131723"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="ef438-102">IInstallReferenceEnum::GetNextInstallReferenceItem, méthode</span><span class="sxs-lookup"><span data-stu-id="ef438-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="ef438-103">Obtient un pointeur vers l’objet [IInstallReferenceItem](iinstallreferenceitem-interface.md) suivant contenu dans cet objet [IInstallReferenceEnum](iinstallreferenceenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ef438-103">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef438-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef438-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef438-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ef438-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="ef438-106">à Pointeur de `IInstallReferenceItem` retourné.</span><span class="sxs-lookup"><span data-stu-id="ef438-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ef438-107">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="ef438-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ef438-108">`dwFlags` doit avoir la valeur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="ef438-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="ef438-109">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="ef438-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ef438-110">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="ef438-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef438-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="ef438-111">Requirements</span></span>  
 <span data-ttu-id="ef438-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef438-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef438-113">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ef438-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ef438-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef438-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef438-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef438-115">See also</span></span>

- [<span data-ttu-id="ef438-116">IInstallReferenceItem, interface</span><span class="sxs-lookup"><span data-stu-id="ef438-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="ef438-117">IInstallReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="ef438-117">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
