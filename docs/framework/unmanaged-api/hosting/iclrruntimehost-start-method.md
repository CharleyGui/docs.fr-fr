---
title: ICLRRuntimeHost::Start, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Start
helpviewer_keywords:
- ICLRRuntimeHost::Start method [.NET Framework hosting]
- Start method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: c0a6dce5-0a8d-42e8-808b-6ca14df9d289
topic_type:
- apiref
ms.openlocfilehash: e5ed1cbb640e760d75e1722871453a0bec283bde
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703902"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="49286-102">ICLRRuntimeHost::Start, méthode</span><span class="sxs-lookup"><span data-stu-id="49286-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="49286-103">Initialise le common language runtime (CLR) dans un processus.</span><span class="sxs-lookup"><span data-stu-id="49286-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49286-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49286-104">Syntax</span></span>  
  
```cpp  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="49286-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="49286-105">Return Value</span></span>  
  
|<span data-ttu-id="49286-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49286-106">HRESULT</span></span>|<span data-ttu-id="49286-107">Description</span><span class="sxs-lookup"><span data-stu-id="49286-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49286-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="49286-108">S_OK</span></span>|<span data-ttu-id="49286-109">`Start`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="49286-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="49286-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="49286-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="49286-111">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="49286-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="49286-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="49286-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="49286-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="49286-113">The call timed out.</span></span>|  
|<span data-ttu-id="49286-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="49286-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="49286-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="49286-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="49286-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="49286-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="49286-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="49286-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="49286-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="49286-118">E_FAIL</span></span>|<span data-ttu-id="49286-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="49286-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="49286-120">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="49286-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="49286-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="49286-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49286-122">Notes</span><span class="sxs-lookup"><span data-stu-id="49286-122">Remarks</span></span>  
 <span data-ttu-id="49286-123">Dans de nombreux scénarios, il n’est pas nécessaire d’appeler `Start` , car le runtime s’initialise automatiquement lors de la première demande d’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="49286-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="49286-124">Toutefois, vous pouvez utiliser `Start` pour spécifier exactement quand le runtime doit être initialisé.</span><span class="sxs-lookup"><span data-stu-id="49286-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49286-125">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="49286-125">Requirements</span></span>  
 <span data-ttu-id="49286-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49286-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49286-127">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="49286-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49286-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="49286-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49286-129">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49286-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49286-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49286-130">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="49286-131">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="49286-131">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
