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
ms.openlocfilehash: e5a1642f968228c5815732ecd470cb8f02a0eb83
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139582"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="0e9d3-102">ICorRuntimeHost::EnumDomains, méthode</span><span class="sxs-lookup"><span data-stu-id="0e9d3-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="0e9d3-103">Obtient un énumérateur pour les domaines du processus en cours.</span><span class="sxs-lookup"><span data-stu-id="0e9d3-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e9d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e9d3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e9d3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e9d3-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="0e9d3-106">à Énumérateur pour les domaines.</span><span class="sxs-lookup"><span data-stu-id="0e9d3-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e9d3-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0e9d3-107">Return Value</span></span>  
  
|<span data-ttu-id="0e9d3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e9d3-108">HRESULT</span></span>|<span data-ttu-id="0e9d3-109">Description</span><span class="sxs-lookup"><span data-stu-id="0e9d3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e9d3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e9d3-110">S_OK</span></span>|<span data-ttu-id="0e9d3-111">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="0e9d3-111">The operation was successful.</span></span>|  
|<span data-ttu-id="0e9d3-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0e9d3-112">S_FALSE</span></span>|<span data-ttu-id="0e9d3-113">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="0e9d3-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="0e9d3-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e9d3-114">E_FAIL</span></span>|<span data-ttu-id="0e9d3-115">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="0e9d3-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0e9d3-116">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="0e9d3-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="0e9d3-117">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0e9d3-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0e9d3-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0e9d3-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0e9d3-119">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="0e9d3-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e9d3-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="0e9d3-120">Requirements</span></span>  
 <span data-ttu-id="0e9d3-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e9d3-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e9d3-122">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0e9d3-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e9d3-123">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0e9d3-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e9d3-124">**Version de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="0e9d3-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e9d3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e9d3-125">See also</span></span>

- [<span data-ttu-id="0e9d3-126">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="0e9d3-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
