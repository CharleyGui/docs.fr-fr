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
ms.openlocfilehash: b1af01559e65bd80fc62cb2eba44bf21d4fa3113
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770909"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="d607c-102">ICorRuntimeHost::Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="d607c-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="d607c-103">Arrête l’exécution de code dans le runtime pour le processus actuel.</span><span class="sxs-lookup"><span data-stu-id="d607c-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d607c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d607c-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d607c-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d607c-105">Return Value</span></span>  
  
|<span data-ttu-id="d607c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d607c-106">HRESULT</span></span>|<span data-ttu-id="d607c-107">Description</span><span class="sxs-lookup"><span data-stu-id="d607c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d607c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d607c-108">S_OK</span></span>|<span data-ttu-id="d607c-109">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="d607c-109">The operation was successful.</span></span>|  
|<span data-ttu-id="d607c-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d607c-110">S_FALSE</span></span>|<span data-ttu-id="d607c-111">L’opération a échoué.</span><span class="sxs-lookup"><span data-stu-id="d607c-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="d607c-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d607c-112">E_FAIL</span></span>|<span data-ttu-id="d607c-113">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d607c-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="d607c-114">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d607c-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="d607c-115">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d607c-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d607c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d607c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d607c-117">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="d607c-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d607c-118">Notes</span><span class="sxs-lookup"><span data-stu-id="d607c-118">Remarks</span></span>  
 <span data-ttu-id="d607c-119">Il est généralement pas nécessaire d’appeler le `Stop` (méthode), étant donné que le code s’arrête quand le processus s’arrête.</span><span class="sxs-lookup"><span data-stu-id="d607c-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d607c-120">Après un appel à `Stop`, le CLR ne peut pas être réinitialisé dans le même processus.</span><span class="sxs-lookup"><span data-stu-id="d607c-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d607c-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d607c-121">Requirements</span></span>  
 <span data-ttu-id="d607c-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d607c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d607c-123">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d607c-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d607c-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d607c-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d607c-125">**Versions du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="d607c-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d607c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d607c-126">See also</span></span>

- [<span data-ttu-id="d607c-127">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="d607c-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
