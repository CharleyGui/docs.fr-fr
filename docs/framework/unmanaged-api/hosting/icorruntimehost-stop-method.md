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
ms.openlocfilehash: 5fcf8bc861b2ef0b8ea9f5a5e46585564cc26615
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127704"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="e847e-102">ICorRuntimeHost::Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="e847e-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="e847e-103">Arrête l’exécution du code dans le runtime pour le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="e847e-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e847e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e847e-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e847e-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e847e-105">Return Value</span></span>  
  
|<span data-ttu-id="e847e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e847e-106">HRESULT</span></span>|<span data-ttu-id="e847e-107">Description</span><span class="sxs-lookup"><span data-stu-id="e847e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e847e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e847e-108">S_OK</span></span>|<span data-ttu-id="e847e-109">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="e847e-109">The operation was successful.</span></span>|  
|<span data-ttu-id="e847e-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e847e-110">S_FALSE</span></span>|<span data-ttu-id="e847e-111">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="e847e-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e847e-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e847e-112">E_FAIL</span></span>|<span data-ttu-id="e847e-113">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e847e-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e847e-114">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e847e-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e847e-115">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e847e-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e847e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e847e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e847e-117">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="e847e-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e847e-118">Notes</span><span class="sxs-lookup"><span data-stu-id="e847e-118">Remarks</span></span>  
 <span data-ttu-id="e847e-119">Il n’est généralement pas nécessaire d’appeler la méthode `Stop`, car le code cesse de s’exécuter lorsque le processus se termine.</span><span class="sxs-lookup"><span data-stu-id="e847e-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e847e-120">Après un appel à `Stop`, le CLR ne peut pas être réinitialisé dans le même processus.</span><span class="sxs-lookup"><span data-stu-id="e847e-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e847e-121">spécifications</span><span class="sxs-lookup"><span data-stu-id="e847e-121">Requirements</span></span>  
 <span data-ttu-id="e847e-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e847e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e847e-123">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e847e-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e847e-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e847e-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e847e-125">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="e847e-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e847e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e847e-126">See also</span></span>

- [<span data-ttu-id="e847e-127">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="e847e-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
