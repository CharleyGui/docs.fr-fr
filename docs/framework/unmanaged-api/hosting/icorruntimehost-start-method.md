---
title: ICorRuntimeHost::Start, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
ms.openlocfilehash: c450d83669a3bc548c15ed5800dc73438b9a84a6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127692"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="bc231-102">ICorRuntimeHost::Start, méthode</span><span class="sxs-lookup"><span data-stu-id="bc231-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="bc231-103">Démarre le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="bc231-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc231-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc231-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bc231-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bc231-105">Return Value</span></span>  
  
|<span data-ttu-id="bc231-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc231-106">HRESULT</span></span>|<span data-ttu-id="bc231-107">Description</span><span class="sxs-lookup"><span data-stu-id="bc231-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc231-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc231-108">S_OK</span></span>|<span data-ttu-id="bc231-109">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="bc231-109">The operation was successful.</span></span>|  
|<span data-ttu-id="bc231-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bc231-110">S_FALSE</span></span>|<span data-ttu-id="bc231-111">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="bc231-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="bc231-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bc231-112">E_FAIL</span></span>|<span data-ttu-id="bc231-113">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="bc231-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="bc231-114">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="bc231-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="bc231-115">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bc231-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bc231-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bc231-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bc231-117">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="bc231-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc231-118">Notes</span><span class="sxs-lookup"><span data-stu-id="bc231-118">Remarks</span></span>  
 <span data-ttu-id="bc231-119">En général, il n’est pas nécessaire d’appeler la méthode `Start`, car le CLR démarre automatiquement lors de la première demande d’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="bc231-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc231-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="bc231-120">Requirements</span></span>  
 <span data-ttu-id="bc231-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc231-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc231-122">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bc231-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc231-123">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bc231-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc231-124">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="bc231-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc231-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc231-125">See also</span></span>

- [<span data-ttu-id="bc231-126">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="bc231-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
