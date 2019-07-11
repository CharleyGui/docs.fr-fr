---
title: ICorRuntimeHost::NextDomain, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf19d322d8e4d0d05993d22b2aa7e46bda7b5a1d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780074"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="e06ee-102">ICorRuntimeHost::NextDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="e06ee-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="e06ee-103">Obtient un pointeur d’interface au domaine suivant dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="e06ee-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e06ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e06ee-104">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e06ee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e06ee-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="e06ee-106">[in] L’énumérateur a été obtenu via un appel à [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="e06ee-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="e06ee-107">[out] Un pointeur d’interface vers le <xref:System._AppDomain?displayProperty=nameWithType> type qui représente le domaine suivant dans l’énumération, ou null, s’il n’existe aucun domaine plus.</span><span class="sxs-lookup"><span data-stu-id="e06ee-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e06ee-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e06ee-108">Return Value</span></span>  
  
|<span data-ttu-id="e06ee-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e06ee-109">HRESULT</span></span>|<span data-ttu-id="e06ee-110">Description</span><span class="sxs-lookup"><span data-stu-id="e06ee-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e06ee-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e06ee-111">S_OK</span></span>|<span data-ttu-id="e06ee-112">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="e06ee-112">The operation was successful.</span></span>|  
|<span data-ttu-id="e06ee-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e06ee-113">S_FALSE</span></span>|<span data-ttu-id="e06ee-114">L’opération a échoué, ou il n’existe aucune davantage de domaines dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="e06ee-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="e06ee-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e06ee-115">E_FAIL</span></span>|<span data-ttu-id="e06ee-116">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e06ee-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e06ee-117">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e06ee-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e06ee-118">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e06ee-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e06ee-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e06ee-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e06ee-120">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="e06ee-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e06ee-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e06ee-121">Requirements</span></span>  
 <span data-ttu-id="e06ee-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e06ee-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e06ee-123">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e06ee-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e06ee-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e06ee-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e06ee-125">**Versions du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="e06ee-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e06ee-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e06ee-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="e06ee-127">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="e06ee-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
