---
title: IHostTask::Start, méthode
ms.date: 03/30/2017
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
ms.openlocfilehash: 4143c3d25dd5262a10b53708a249910cc79f5314
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720436"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="50869-102">IHostTask::Start, méthode</span><span class="sxs-lookup"><span data-stu-id="50869-102">IHostTask::Start Method</span></span>

<span data-ttu-id="50869-103">Demande que l’hôte déplace la tâche représentée par l’instance [IHostTask](ihosttask-interface.md) actuelle d’un état suspendu à un état actif dans lequel le code peut être exécuté.</span><span class="sxs-lookup"><span data-stu-id="50869-103">Requests that the host move the task represented by the current [IHostTask](ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50869-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50869-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="50869-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="50869-105">Return Value</span></span>  
  
|<span data-ttu-id="50869-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50869-106">HRESULT</span></span>|<span data-ttu-id="50869-107">Description</span><span class="sxs-lookup"><span data-stu-id="50869-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50869-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="50869-108">S_OK</span></span>|<span data-ttu-id="50869-109">Le démarrage a été retourné.</span><span class="sxs-lookup"><span data-stu-id="50869-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="50869-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50869-110">E_FAIL</span></span>|<span data-ttu-id="50869-111">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="50869-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50869-112">Quand une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="50869-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="50869-113">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="50869-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50869-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="50869-114">Remarks</span></span>  

 <span data-ttu-id="50869-115">`Start` retourne toujours une valeur HRESULT de S_OK, sauf dans les cas où une défaillance catastrophique s’est produite.</span><span class="sxs-lookup"><span data-stu-id="50869-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50869-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="50869-116">Requirements</span></span>  

 <span data-ttu-id="50869-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50869-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50869-118">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="50869-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50869-119">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50869-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50869-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50869-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50869-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50869-121">See also</span></span>

- [<span data-ttu-id="50869-122">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="50869-122">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="50869-123">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="50869-123">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="50869-124">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="50869-124">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="50869-125">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="50869-125">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
