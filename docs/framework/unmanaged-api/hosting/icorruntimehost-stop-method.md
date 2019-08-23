---
title: ICorRuntimeHost::Stop, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca51b87e7afc8e9e48d541a32b3bd60a19a5ff70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965972"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="d3796-102">ICorRuntimeHost::Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="d3796-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="d3796-103">Arrête l’exécution du code dans le runtime pour le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="d3796-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3796-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3796-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d3796-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d3796-105">Return Value</span></span>  
  
|<span data-ttu-id="d3796-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d3796-106">HRESULT</span></span>|<span data-ttu-id="d3796-107">Description</span><span class="sxs-lookup"><span data-stu-id="d3796-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d3796-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d3796-108">S_OK</span></span>|<span data-ttu-id="d3796-109">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="d3796-109">The operation was successful.</span></span>|  
|<span data-ttu-id="d3796-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d3796-110">S_FALSE</span></span>|<span data-ttu-id="d3796-111">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="d3796-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="d3796-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d3796-112">E_FAIL</span></span>|<span data-ttu-id="d3796-113">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d3796-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="d3796-114">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d3796-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="d3796-115">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d3796-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d3796-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d3796-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d3796-117">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="d3796-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3796-118">Notes</span><span class="sxs-lookup"><span data-stu-id="d3796-118">Remarks</span></span>  
 <span data-ttu-id="d3796-119">Il n’est généralement pas nécessaire d' `Stop` appeler la méthode, car le code cesse de s’exécuter lorsque le processus se termine.</span><span class="sxs-lookup"><span data-stu-id="d3796-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3796-120">Après un appel à `Stop`, le CLR ne peut pas être réinitialisé dans le même processus.</span><span class="sxs-lookup"><span data-stu-id="d3796-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3796-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d3796-121">Requirements</span></span>  
 <span data-ttu-id="d3796-122">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3796-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3796-123">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d3796-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3796-124">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d3796-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3796-125">**Versions de .NET Framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="d3796-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3796-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3796-126">See also</span></span>

- [<span data-ttu-id="d3796-127">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="d3796-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
