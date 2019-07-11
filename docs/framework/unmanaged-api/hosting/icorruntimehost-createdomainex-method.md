---
title: ICorRuntimeHost::CreateDomainEx, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e51c5cda8eca1737e2daab4cbe94a78433c8608
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762119"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="ffbf5-102">ICorRuntimeHost::CreateDomainEx, méthode</span><span class="sxs-lookup"><span data-stu-id="ffbf5-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="ffbf5-103">Crée un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-103">Creates an application domain.</span></span> <span data-ttu-id="ffbf5-104">L’appelant reçoit un pointeur d’interface, de type <xref:System._AppDomain>, à une instance de type <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ffbf5-105">Cette méthode permet à l’appelant de passer une instance IAppDomainSetup pour configurer des fonctionnalités supplémentaires de retourné <xref:System._AppDomain> instance.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffbf5-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ffbf5-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffbf5-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ffbf5-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="ffbf5-108">[in] Un paramètre optionnel utilisé pour donner un nom convivial au domaine.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="ffbf5-109">Ce nom convivial peut être affiché dans les interfaces utilisateur telles que les débogueurs pour identifier le domaine.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="ffbf5-110">[in] Un pointeur d’interface facultatif de type `IAppDomainSetup`, obtenue par un appel à la [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="ffbf5-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="ffbf5-111">[in] Tableau facultatif de pointeurs vers `IIdentity` instances qui représentent la preuve mappée via la stratégie de sécurité pour établir un jeu d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="ffbf5-112">Un `IIdentity` objet peut être obtenu en appelant le [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="ffbf5-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="ffbf5-113">[out] Un pointeur d’interface de type <xref:System._AppDomain> à une instance de <xref:System.AppDomain?displayProperty=nameWithType> qui peut être utilisé pour contrôler davantage le domaine.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffbf5-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ffbf5-114">Return Value</span></span>  
  
|<span data-ttu-id="ffbf5-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ffbf5-115">HRESULT</span></span>|<span data-ttu-id="ffbf5-116">Description</span><span class="sxs-lookup"><span data-stu-id="ffbf5-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ffbf5-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="ffbf5-117">S_OK</span></span>|<span data-ttu-id="ffbf5-118">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-118">The operation was successful.</span></span>|  
|<span data-ttu-id="ffbf5-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ffbf5-119">S_FALSE</span></span>|<span data-ttu-id="ffbf5-120">L’opération a échoué.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="ffbf5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ffbf5-121">E_FAIL</span></span>|<span data-ttu-id="ffbf5-122">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ffbf5-123">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="ffbf5-124">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ffbf5-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ffbf5-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ffbf5-126">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffbf5-127">Notes</span><span class="sxs-lookup"><span data-stu-id="ffbf5-127">Remarks</span></span>  
 <span data-ttu-id="ffbf5-128">`CreateDomainEx` étend les capacités de [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) en permettant à l’appelant de passer un `IAppDomainSetup` instance avec les valeurs de propriété pour configurer le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="ffbf5-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffbf5-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ffbf5-129">Requirements</span></span>  
 <span data-ttu-id="ffbf5-130">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffbf5-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffbf5-131">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ffbf5-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffbf5-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ffbf5-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffbf5-133">**Version du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="ffbf5-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffbf5-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffbf5-134">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="ffbf5-135">CreateDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="ffbf5-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="ffbf5-136">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="ffbf5-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
