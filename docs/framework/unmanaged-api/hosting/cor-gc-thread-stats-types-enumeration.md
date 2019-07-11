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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a984e8645bec0f58d8a31965b762e0a3a190ba59
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768020"
---
# <a name="corgcthreadstatstypes-enumeration"></a><span data-ttu-id="298eb-102">COR_GC_THREAD_STATS_TYPES (énumération)</span><span class="sxs-lookup"><span data-stu-id="298eb-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="298eb-103">Indique les statistiques de garbage collection pour un thread.</span><span class="sxs-lookup"><span data-stu-id="298eb-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="298eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="298eb-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="298eb-105">Membres</span><span class="sxs-lookup"><span data-stu-id="298eb-105">Members</span></span>  
  
|<span data-ttu-id="298eb-106">Membre</span><span class="sxs-lookup"><span data-stu-id="298eb-106">Member</span></span>|<span data-ttu-id="298eb-107">Description</span><span class="sxs-lookup"><span data-stu-id="298eb-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="298eb-108">Le thread a octets qui ont été promus dans le garbage collection le plus récent.</span><span class="sxs-lookup"><span data-stu-id="298eb-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="298eb-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="298eb-109">Requirements</span></span>  
 <span data-ttu-id="298eb-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="298eb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="298eb-111">**En-tête :** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="298eb-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="298eb-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="298eb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="298eb-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="298eb-113">See also</span></span>

- [<span data-ttu-id="298eb-114">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="298eb-114">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
