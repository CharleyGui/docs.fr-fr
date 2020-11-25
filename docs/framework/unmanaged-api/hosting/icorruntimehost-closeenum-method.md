---
title: ICorRuntimeHost::CloseEnum, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
ms.openlocfilehash: d3748621474373fee8248496d48414ff67c699d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715693"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="8cd91-102">ICorRuntimeHost::CloseEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="8cd91-102">ICorRuntimeHost::CloseEnum Method</span></span>

<span data-ttu-id="8cd91-103">Réinitialise un énumérateur de domaine au début de la liste de domaines.</span><span class="sxs-lookup"><span data-stu-id="8cd91-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cd91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cd91-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cd91-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8cd91-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="8cd91-106">dans Énumérateur à réinitialiser.</span><span class="sxs-lookup"><span data-stu-id="8cd91-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cd91-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="8cd91-107">Return Value</span></span>  
  
|<span data-ttu-id="8cd91-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8cd91-108">HRESULT</span></span>|<span data-ttu-id="8cd91-109">Description</span><span class="sxs-lookup"><span data-stu-id="8cd91-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8cd91-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8cd91-110">S_OK</span></span>|<span data-ttu-id="8cd91-111">L'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="8cd91-111">The operation was successful.</span></span>|  
|<span data-ttu-id="8cd91-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8cd91-112">S_FALSE</span></span>|<span data-ttu-id="8cd91-113">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="8cd91-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="8cd91-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8cd91-114">E_FAIL</span></span>|<span data-ttu-id="8cd91-115">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="8cd91-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="8cd91-116">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="8cd91-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="8cd91-117">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8cd91-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8cd91-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8cd91-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8cd91-119">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="8cd91-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8cd91-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8cd91-120">Requirements</span></span>  

 <span data-ttu-id="8cd91-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cd91-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cd91-122">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8cd91-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8cd91-123">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8cd91-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8cd91-124">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="8cd91-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cd91-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cd91-125">See also</span></span>

- [<span data-ttu-id="8cd91-126">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="8cd91-126">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="8cd91-127">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="8cd91-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
