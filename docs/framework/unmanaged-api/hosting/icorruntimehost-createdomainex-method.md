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
ms.openlocfilehash: 4e5856fbcda83c1dd30559c6f59f63495faea78d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762342"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="1eaf0-102">ICorRuntimeHost::CreateDomainEx, méthode</span><span class="sxs-lookup"><span data-stu-id="1eaf0-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="1eaf0-103">Crée un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-103">Creates an application domain.</span></span> <span data-ttu-id="1eaf0-104">L’appelant reçoit un pointeur d’interface, de type <xref:System._AppDomain> , à une instance de type <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1eaf0-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1eaf0-105">Cette méthode permet à l’appelant de passer une instance IAppDomainSetup pour configurer des fonctionnalités supplémentaires de l’instance retournée <xref:System._AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="1eaf0-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eaf0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1eaf0-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1eaf0-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1eaf0-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="1eaf0-108">dans Paramètre facultatif utilisé pour attribuer un nom convivial au domaine.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="1eaf0-109">Ce nom convivial peut être affiché dans les interfaces utilisateur, telles que les débogueurs, pour identifier le domaine.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="1eaf0-110">dans Pointeur d’interface facultatif de type `IAppDomainSetup` , obtenu par un appel à la méthode [ICorRuntimeHost :: CreateDomainSetup,](icorruntimehost-createdomainsetup-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1eaf0-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="1eaf0-111">dans Tableau facultatif de pointeurs vers des `IIdentity` instances qui représentent une preuve mappée par le biais d’une stratégie de sécurité pour établir un jeu d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="1eaf0-112">Un `IIdentity` objet peut être obtenu en appelant la méthode [CreateEvidence,](icorruntimehost-createevidence-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1eaf0-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="1eaf0-113">à Pointeur d’interface de type <xref:System._AppDomain> vers une instance de <xref:System.AppDomain?displayProperty=nameWithType> qui peut être utilisée pour mieux contrôler le domaine.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1eaf0-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1eaf0-114">Return Value</span></span>  
  
|<span data-ttu-id="1eaf0-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1eaf0-115">HRESULT</span></span>|<span data-ttu-id="1eaf0-116">Description</span><span class="sxs-lookup"><span data-stu-id="1eaf0-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1eaf0-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="1eaf0-117">S_OK</span></span>|<span data-ttu-id="1eaf0-118">L'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-118">The operation was successful.</span></span>|  
|<span data-ttu-id="1eaf0-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1eaf0-119">S_FALSE</span></span>|<span data-ttu-id="1eaf0-120">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1eaf0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1eaf0-121">E_FAIL</span></span>|<span data-ttu-id="1eaf0-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1eaf0-123">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1eaf0-124">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1eaf0-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1eaf0-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1eaf0-126">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1eaf0-127">Notes</span><span class="sxs-lookup"><span data-stu-id="1eaf0-127">Remarks</span></span>  
 <span data-ttu-id="1eaf0-128">`CreateDomainEx`étend les fonctionnalités de [CreateDomain](icorruntimehost-createdomain-method.md) en permettant à l’appelant de passer une `IAppDomainSetup` instance avec des valeurs de propriété pour configurer le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="1eaf0-128">`CreateDomainEx` extends the capabilities of [CreateDomain](icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eaf0-129">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="1eaf0-129">Requirements</span></span>  
 <span data-ttu-id="1eaf0-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1eaf0-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eaf0-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1eaf0-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1eaf0-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1eaf0-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1eaf0-133">**Version de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="1eaf0-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eaf0-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1eaf0-134">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="1eaf0-135">CreateDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="1eaf0-135">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="1eaf0-136">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="1eaf0-136">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
