---
title: ICLRRuntimeHost::Stop, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type:
- apiref
ms.openlocfilehash: 0b59532d18848f1896977aa37f0a9f54a939aa75
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120376"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="37094-102">ICLRRuntimeHost::Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="37094-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="37094-103">Arrête l’exécution du code par le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="37094-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="37094-104">Cette méthode ne libère pas les ressources de l’hôte, ne décharge pas les domaines d’application ou ne détruit pas les threads.</span><span class="sxs-lookup"><span data-stu-id="37094-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="37094-105">Vous devez terminer le processus pour libérer ces ressources.</span><span class="sxs-lookup"><span data-stu-id="37094-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37094-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37094-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="37094-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="37094-107">Return Value</span></span>  
  
|<span data-ttu-id="37094-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37094-108">HRESULT</span></span>|<span data-ttu-id="37094-109">Description</span><span class="sxs-lookup"><span data-stu-id="37094-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37094-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="37094-110">S_OK</span></span>|<span data-ttu-id="37094-111">`Stop` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="37094-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="37094-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37094-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37094-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="37094-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="37094-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="37094-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="37094-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="37094-115">The call timed out.</span></span>|  
|<span data-ttu-id="37094-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="37094-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="37094-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="37094-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="37094-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="37094-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="37094-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="37094-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="37094-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37094-120">E_FAIL</span></span>|<span data-ttu-id="37094-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="37094-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="37094-122">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="37094-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="37094-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="37094-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37094-124">spécifications</span><span class="sxs-lookup"><span data-stu-id="37094-124">Requirements</span></span>  
 <span data-ttu-id="37094-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37094-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37094-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="37094-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37094-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="37094-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37094-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37094-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37094-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37094-129">See also</span></span>

- [<span data-ttu-id="37094-130">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="37094-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
