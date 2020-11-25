---
title: ICLRDomainManager::SetAppDomainManagerType, méthode
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
ms.openlocfilehash: 7c6b328793e6437682ad8d642e611be30e7b0fe6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702145"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a><span data-ttu-id="50f48-102">ICLRDomainManager::SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="50f48-102">ICLRDomainManager::SetAppDomainManagerType Method</span></span>

<span data-ttu-id="50f48-103">Spécifie le type, dérivé de la <xref:System.AppDomainManager?displayProperty=nameWithType> classe, du gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut.</span><span class="sxs-lookup"><span data-stu-id="50f48-103">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50f48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50f48-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50f48-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="50f48-105">Parameters</span></span>  

 `wszAppDomainManagerAssembly`  
 <span data-ttu-id="50f48-106">dans Nom complet de l’assembly qui contient le type de gestionnaire de domaine d’application ; par exemple : « AdMgrExample, version = 1.0.0.0, culture = neutral, PublicKeyToken = 6856bccf150f00b3 ».</span><span class="sxs-lookup"><span data-stu-id="50f48-106">[in] The display name of the assembly that contains the application domain manager type; for example: "AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3".</span></span>  
  
 `wszAppDomainManagerType`  
 <span data-ttu-id="50f48-107">dans Nom de type du gestionnaire de domaine d’application, y compris l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="50f48-107">[in] The type name of the application domain manager, including the namespace.</span></span>  
  
 `dwInitializeDomainFlags`  
 <span data-ttu-id="50f48-108">dans Combinaison de valeurs d’énumération [EInitializeNewDomainFlags,](einitializenewdomainflags-enumeration.md) qui fournissent des informations sur le gestionnaire de domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="50f48-108">[in] A combination of [EInitializeNewDomainFlags](einitializenewdomainflags-enumeration.md) enumeration values that provide information about the application domain manager.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50f48-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="50f48-109">Return Value</span></span>  

 <span data-ttu-id="50f48-110">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="50f48-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="50f48-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50f48-111">HRESULT</span></span>|<span data-ttu-id="50f48-112">Description</span><span class="sxs-lookup"><span data-stu-id="50f48-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50f48-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="50f48-113">S_OK</span></span>|<span data-ttu-id="50f48-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="50f48-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="50f48-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50f48-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50f48-116">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="50f48-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50f48-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="50f48-117">Remarks</span></span>  

 <span data-ttu-id="50f48-118">Actuellement, la seule valeur définie pour `dwInitializeDomainFlags` est `eInitializeNewDomainFlags_NoSecurityChanges` , qui indique à l’Common Language Runtime (CLR) que le gestionnaire de domaine d’application ne modifiera pas les paramètres de sécurité pendant l’exécution de la <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="50f48-118">Currently, the only defined value for `dwInitializeDomainFlags` is `eInitializeNewDomainFlags_NoSecurityChanges`, which tells the common language runtime (CLR) that the application domain manager will not modify security settings during the execution of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="50f48-119">Cela permet au CLR d’optimiser le chargement des assemblys qui ont l' <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut conditionnel (APTCA).</span><span class="sxs-lookup"><span data-stu-id="50f48-119">This allows the CLR to optimize the loading of assemblies that have the conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) attribute.</span></span> <span data-ttu-id="50f48-120">Cela peut entraîner une amélioration significative du temps de démarrage si la fermeture transitive de cet ensemble d’assemblys est importante.</span><span class="sxs-lookup"><span data-stu-id="50f48-120">This can result in a significant improvement in startup time if the transitive closure of this set of assemblies is large.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="50f48-121">Si l’hôte spécifie `eInitializeNewDomainFlags_NoSecurityChanges` pour le gestionnaire de domaine d’application, une <xref:System.InvalidOperationException> exception est levée si une tentative est faite pour modifier la sécurité du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="50f48-121">If the host specifies `eInitializeNewDomainFlags_NoSecurityChanges` for the application domain manager, an <xref:System.InvalidOperationException> is thrown if any attempt is made to modify the security of the application domain.</span></span>  
  
 <span data-ttu-id="50f48-122">L’appel de la méthode [ICLRControl :: SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)équivaut à l’appel `ICLRDomainManager::SetAppDomainManagerType` de avec `eInitializeNewDomainFlags_None` .</span><span class="sxs-lookup"><span data-stu-id="50f48-122">Calling the [ICLRControl::SetAppDomainManagerType](iclrcontrol-setappdomainmanagertype-method.md)method is equivalent to calling `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50f48-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="50f48-123">Requirements</span></span>  

 <span data-ttu-id="50f48-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50f48-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50f48-125">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="50f48-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="50f48-126">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="50f48-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50f48-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50f48-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f48-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50f48-128">See also</span></span>

- [<span data-ttu-id="50f48-129">Hébergement</span><span class="sxs-lookup"><span data-stu-id="50f48-129">Hosting</span></span>](index.md)
- [<span data-ttu-id="50f48-130">ICLRDomainManager, interface</span><span class="sxs-lookup"><span data-stu-id="50f48-130">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)
- [<span data-ttu-id="50f48-131">EInitializeNewDomainFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="50f48-131">EInitializeNewDomainFlags Enumeration</span></span>](einitializenewdomainflags-enumeration.md)
