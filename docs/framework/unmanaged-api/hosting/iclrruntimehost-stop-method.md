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
ms.openlocfilehash: 55cd444ffedc92ba74239421ae548ffd930e6ab7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703932"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="47016-102">ICLRRuntimeHost::Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="47016-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="47016-103">Arrête l’exécution du code par le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="47016-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="47016-104">Cette méthode ne libère pas les ressources de l’hôte, ne décharge pas les domaines d’application ou ne détruit pas les threads.</span><span class="sxs-lookup"><span data-stu-id="47016-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="47016-105">Vous devez terminer le processus pour libérer ces ressources.</span><span class="sxs-lookup"><span data-stu-id="47016-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47016-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47016-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="47016-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="47016-107">Return Value</span></span>  
  
|<span data-ttu-id="47016-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="47016-108">HRESULT</span></span>|<span data-ttu-id="47016-109">Description</span><span class="sxs-lookup"><span data-stu-id="47016-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47016-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="47016-110">S_OK</span></span>|<span data-ttu-id="47016-111">`Stop`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="47016-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="47016-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="47016-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="47016-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="47016-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="47016-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="47016-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="47016-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="47016-115">The call timed out.</span></span>|  
|<span data-ttu-id="47016-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="47016-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="47016-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="47016-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="47016-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="47016-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="47016-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="47016-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="47016-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="47016-120">E_FAIL</span></span>|<span data-ttu-id="47016-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="47016-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="47016-122">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="47016-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="47016-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="47016-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="47016-124">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="47016-124">Requirements</span></span>  
 <span data-ttu-id="47016-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47016-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47016-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="47016-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47016-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="47016-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47016-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47016-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47016-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47016-129">See also</span></span>

- [<span data-ttu-id="47016-130">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="47016-130">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
