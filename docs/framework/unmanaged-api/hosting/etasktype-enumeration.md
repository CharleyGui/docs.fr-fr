---
title: ETaskType, énumération
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
ms.openlocfilehash: bc956827ad59fc655137e4147e6d98b6d097d470
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138187"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="80c57-102">ETaskType, énumération</span><span class="sxs-lookup"><span data-stu-id="80c57-102">ETaskType Enumeration</span></span>
<span data-ttu-id="80c57-103">Contient des valeurs qui indiquent le type de tâche représenté par une interface [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) ou [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="80c57-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) or an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80c57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80c57-104">Syntax</span></span>  
  
```cpp  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a><span data-ttu-id="80c57-105">Membres</span><span class="sxs-lookup"><span data-stu-id="80c57-105">Members</span></span>  
  
|<span data-ttu-id="80c57-106">Membre</span><span class="sxs-lookup"><span data-stu-id="80c57-106">Member</span></span>|<span data-ttu-id="80c57-107">Description</span><span class="sxs-lookup"><span data-stu-id="80c57-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="80c57-108">L’interface représente une tâche de déchargement de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="80c57-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="80c57-109">L’interface représente une tâche d’assistance du débogueur.</span><span class="sxs-lookup"><span data-stu-id="80c57-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="80c57-110">L’interface représente une tâche de finaliseur.</span><span class="sxs-lookup"><span data-stu-id="80c57-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="80c57-111">L’interface représente une tâche garbage collection.</span><span class="sxs-lookup"><span data-stu-id="80c57-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="80c57-112">L’interface représente une tâche de thread de la porte.</span><span class="sxs-lookup"><span data-stu-id="80c57-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="80c57-113">L’interface représente une tâche de thread d’e/s ou une tâche de thread de terminaison de port.</span><span class="sxs-lookup"><span data-stu-id="80c57-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="80c57-114">L’interface représente une tâche de thread de minuterie.</span><span class="sxs-lookup"><span data-stu-id="80c57-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="80c57-115">L’interface représente une tâche de thread d’attente.</span><span class="sxs-lookup"><span data-stu-id="80c57-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="80c57-116">L’interface représente une tâche de thread de travail.</span><span class="sxs-lookup"><span data-stu-id="80c57-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="80c57-117">La tâche est inconnue.</span><span class="sxs-lookup"><span data-stu-id="80c57-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="80c57-118">L’interface représente une tâche utilisateur.</span><span class="sxs-lookup"><span data-stu-id="80c57-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80c57-119">spécifications</span><span class="sxs-lookup"><span data-stu-id="80c57-119">Requirements</span></span>  
 <span data-ttu-id="80c57-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80c57-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80c57-121">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="80c57-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80c57-122">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="80c57-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80c57-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80c57-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c57-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80c57-124">See also</span></span>

- [<span data-ttu-id="80c57-125">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="80c57-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
