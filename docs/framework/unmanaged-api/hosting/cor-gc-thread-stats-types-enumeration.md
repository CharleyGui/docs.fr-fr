---
title: COR_GC_THREAD_STATS_TYPES (énumération)
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS_TYPES
helpviewer_keywords:
- COR_GC_THREAD_STATS_TYPES enumeration [.NET Framework hosting]
ms.assetid: aa227704-0ab1-4b08-aee2-1f439762162e
topic_type:
- apiref
ms.openlocfilehash: 2206499cad9be2a29f485ee66d468accbe00b5f5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616674"
---
# <a name="cor_gc_thread_stats_types-enumeration"></a><span data-ttu-id="644a5-102">COR_GC_THREAD_STATS_TYPES (énumération)</span><span class="sxs-lookup"><span data-stu-id="644a5-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="644a5-103">Indique les statistiques de garbage collection d’un thread.</span><span class="sxs-lookup"><span data-stu-id="644a5-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="644a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="644a5-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="644a5-105">Membres</span><span class="sxs-lookup"><span data-stu-id="644a5-105">Members</span></span>  
  
|<span data-ttu-id="644a5-106">Membre</span><span class="sxs-lookup"><span data-stu-id="644a5-106">Member</span></span>|<span data-ttu-id="644a5-107">Description</span><span class="sxs-lookup"><span data-stu-id="644a5-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="644a5-108">Le thread a des octets qui ont été promus dans le garbage collection le plus récent.</span><span class="sxs-lookup"><span data-stu-id="644a5-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="644a5-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="644a5-109">Requirements</span></span>  
 <span data-ttu-id="644a5-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="644a5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="644a5-111">**En-tête :** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="644a5-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="644a5-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="644a5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="644a5-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="644a5-113">See also</span></span>

- [<span data-ttu-id="644a5-114">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="644a5-114">Hosting Enumerations</span></span>](hosting-enumerations.md)
