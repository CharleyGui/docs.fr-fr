---
title: IGCHost::GetThreadStats, méthode
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
ms.openlocfilehash: 4a7a2da58e197749d492f24c7a12134508efef57
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805231"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="ce1e0-102">IGCHost::GetThreadStats, méthode</span><span class="sxs-lookup"><span data-stu-id="ce1e0-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="ce1e0-103">Obtient les statistiques par thread pour garbage collection.</span><span class="sxs-lookup"><span data-stu-id="ce1e0-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce1e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce1e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce1e0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ce1e0-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="ce1e0-106">dans Pointeur vers un cookie Fiber qui spécifie le thread pour lequel les statistiques doivent être récupérées.</span><span class="sxs-lookup"><span data-stu-id="ce1e0-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="ce1e0-107">[in, out] Pointeur vers une structure [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) qui contient les statistiques garbage collection pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="ce1e0-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce1e0-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ce1e0-108">Requirements</span></span>  
 <span data-ttu-id="ce1e0-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce1e0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce1e0-110">**En-tête :** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="ce1e0-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="ce1e0-111">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ce1e0-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce1e0-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce1e0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce1e0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce1e0-113">See also</span></span>

- [<span data-ttu-id="ce1e0-114">IGCHost, interface</span><span class="sxs-lookup"><span data-stu-id="ce1e0-114">IGCHost Interface</span></span>](igchost-interface.md)
