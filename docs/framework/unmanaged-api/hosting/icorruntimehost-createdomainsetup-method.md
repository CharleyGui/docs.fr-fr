---
title: ICorRuntimeHost::CreateDomainSetup, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f8e9284283247ec46a225470ae3063dac539f43
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780017"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="1a11e-102">ICorRuntimeHost::CreateDomainSetup, méthode</span><span class="sxs-lookup"><span data-stu-id="1a11e-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="1a11e-103">Obtient un pointeur d’interface de type IAppDomainSetup à un <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="1a11e-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="1a11e-104">`IAppDomainSetup` Fournit des méthodes pour configurer les aspects d’un domaine d’application avant sa création.</span><span class="sxs-lookup"><span data-stu-id="1a11e-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a11e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a11e-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a11e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1a11e-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="1a11e-107">[out] Un pointeur d’interface vers un <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="1a11e-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="1a11e-108">Ce paramètre est de type `IUnknown`, de sorte que les appelants doivent généralement appeler `QueryInterface` sur ce pointeur pour obtenir un pointeur d’interface de type `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="1a11e-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a11e-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1a11e-109">Return Value</span></span>  
  
|<span data-ttu-id="1a11e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1a11e-110">HRESULT</span></span>|<span data-ttu-id="1a11e-111">Description</span><span class="sxs-lookup"><span data-stu-id="1a11e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1a11e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="1a11e-112">S_OK</span></span>|<span data-ttu-id="1a11e-113">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="1a11e-113">The operation was successful.</span></span>|  
|<span data-ttu-id="1a11e-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1a11e-114">S_FALSE</span></span>|<span data-ttu-id="1a11e-115">L’opération a échoué.</span><span class="sxs-lookup"><span data-stu-id="1a11e-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1a11e-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1a11e-116">E_FAIL</span></span>|<span data-ttu-id="1a11e-117">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1a11e-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1a11e-118">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1a11e-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1a11e-119">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1a11e-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1a11e-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1a11e-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1a11e-121">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="1a11e-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a11e-122">Notes</span><span class="sxs-lookup"><span data-stu-id="1a11e-122">Remarks</span></span>  
 <span data-ttu-id="1a11e-123">Le pointeur retourné par cette méthode est généralement passé en tant que paramètre à la [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="1a11e-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a11e-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1a11e-124">Requirements</span></span>  
 <span data-ttu-id="1a11e-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a11e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a11e-126">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1a11e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a11e-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a11e-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a11e-128">**Version du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="1a11e-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a11e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a11e-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="1a11e-130">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="1a11e-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
