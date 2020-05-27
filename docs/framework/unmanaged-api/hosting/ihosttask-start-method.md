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
ms.openlocfilehash: a4e8211f091b2a3a4f24d8350f6d7dbe7d7920af
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842385"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="adaf2-102">IHostTask::Start, méthode</span><span class="sxs-lookup"><span data-stu-id="adaf2-102">IHostTask::Start Method</span></span>
<span data-ttu-id="adaf2-103">Demande que l’hôte déplace la tâche représentée par l’instance [IHostTask](ihosttask-interface.md) actuelle d’un état suspendu à un état actif dans lequel le code peut être exécuté.</span><span class="sxs-lookup"><span data-stu-id="adaf2-103">Requests that the host move the task represented by the current [IHostTask](ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adaf2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adaf2-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="adaf2-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="adaf2-105">Return Value</span></span>  
  
|<span data-ttu-id="adaf2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="adaf2-106">HRESULT</span></span>|<span data-ttu-id="adaf2-107">Description</span><span class="sxs-lookup"><span data-stu-id="adaf2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="adaf2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="adaf2-108">S_OK</span></span>|<span data-ttu-id="adaf2-109">Le démarrage a été retourné.</span><span class="sxs-lookup"><span data-stu-id="adaf2-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="adaf2-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="adaf2-110">E_FAIL</span></span>|<span data-ttu-id="adaf2-111">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="adaf2-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="adaf2-112">Quand une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="adaf2-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="adaf2-113">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="adaf2-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adaf2-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="adaf2-114">Remarks</span></span>  
 <span data-ttu-id="adaf2-115">`Start`retourne toujours une valeur HRESULT de S_OK, sauf dans les cas où une défaillance catastrophique s’est produite.</span><span class="sxs-lookup"><span data-stu-id="adaf2-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adaf2-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="adaf2-116">Requirements</span></span>  
 <span data-ttu-id="adaf2-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adaf2-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adaf2-118">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="adaf2-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="adaf2-119">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="adaf2-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="adaf2-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adaf2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adaf2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adaf2-121">See also</span></span>

- [<span data-ttu-id="adaf2-122">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="adaf2-122">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="adaf2-123">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="adaf2-123">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="adaf2-124">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="adaf2-124">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="adaf2-125">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="adaf2-125">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
