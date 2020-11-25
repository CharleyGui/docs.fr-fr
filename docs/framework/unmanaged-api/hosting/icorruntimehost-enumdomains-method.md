---
title: ICorRuntimeHost::EnumDomains, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.EnumDomains
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type:
- apiref
ms.openlocfilehash: f4338429dc24bf5196b92d3f18e73c98442f61e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720660"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="59b6d-102">ICorRuntimeHost::EnumDomains, méthode</span><span class="sxs-lookup"><span data-stu-id="59b6d-102">ICorRuntimeHost::EnumDomains Method</span></span>

<span data-ttu-id="59b6d-103">Obtient un énumérateur pour les domaines du processus en cours.</span><span class="sxs-lookup"><span data-stu-id="59b6d-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59b6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59b6d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59b6d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="59b6d-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="59b6d-106">à Énumérateur pour les domaines.</span><span class="sxs-lookup"><span data-stu-id="59b6d-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59b6d-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="59b6d-107">Return Value</span></span>  
  
|<span data-ttu-id="59b6d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="59b6d-108">HRESULT</span></span>|<span data-ttu-id="59b6d-109">Description</span><span class="sxs-lookup"><span data-stu-id="59b6d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="59b6d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="59b6d-110">S_OK</span></span>|<span data-ttu-id="59b6d-111">L'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="59b6d-111">The operation was successful.</span></span>|  
|<span data-ttu-id="59b6d-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="59b6d-112">S_FALSE</span></span>|<span data-ttu-id="59b6d-113">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="59b6d-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="59b6d-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="59b6d-114">E_FAIL</span></span>|<span data-ttu-id="59b6d-115">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="59b6d-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="59b6d-116">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="59b6d-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="59b6d-117">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="59b6d-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="59b6d-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="59b6d-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="59b6d-119">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="59b6d-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59b6d-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="59b6d-120">Requirements</span></span>  

 <span data-ttu-id="59b6d-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59b6d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59b6d-122">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="59b6d-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59b6d-123">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="59b6d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59b6d-124">**Version de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="59b6d-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59b6d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59b6d-125">See also</span></span>

- [<span data-ttu-id="59b6d-126">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="59b6d-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
