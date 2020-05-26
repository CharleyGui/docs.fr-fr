---
title: IGCHost::GetStats, méthode
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
ms.openlocfilehash: 67668aa7ff9faf035a047e485a8a3c8a451f45b9
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805247"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="1d9b9-102">IGCHost::GetStats, méthode</span><span class="sxs-lookup"><span data-stu-id="1d9b9-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="1d9b9-103">Obtient les statistiques de l’état actuel du système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1d9b9-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d9b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d9b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d9b9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1d9b9-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="1d9b9-106">[in, out] Pointeur vers une structure [COR_GC_STATS](cor-gc-stats-structure.md) qui contient les statistiques relatives à l’état actuel du système garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1d9b9-106">[in, out] A pointer to a [COR_GC_STATS](cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d9b9-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1d9b9-107">Remarks</span></span>  
 <span data-ttu-id="1d9b9-108">Les statistiques peuvent être utilisées par un système d’allocation intelligent pour aider le système garbage collection fonctionner.</span><span class="sxs-lookup"><span data-stu-id="1d9b9-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="1d9b9-109">Par exemple, le système d’allocation peut déterminer, après avoir examiné les statistiques, qu’il a besoin d’ajouter de la mémoire ou de forcer une collection.</span><span class="sxs-lookup"><span data-stu-id="1d9b9-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d9b9-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1d9b9-110">Requirements</span></span>  
 <span data-ttu-id="1d9b9-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d9b9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d9b9-112">**En-tête :** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="1d9b9-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="1d9b9-113">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1d9b9-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d9b9-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d9b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d9b9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d9b9-115">See also</span></span>

- [<span data-ttu-id="1d9b9-116">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="1d9b9-116">IGCHost Interface</span></span>](igchost-interface.md)
