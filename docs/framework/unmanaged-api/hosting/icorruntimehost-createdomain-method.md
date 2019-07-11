---
title: ICorRuntimeHost::CreateDomain, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fdacb690b31e7b9930825e5d54ef8fc95bb3a5a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762134"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="c5830-102">ICorRuntimeHost::CreateDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="c5830-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="c5830-103">Crée un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="c5830-103">Creates an application domain.</span></span> <span data-ttu-id="c5830-104">L’appelant reçoit un pointeur d’interface de type <xref:System._AppDomain> à une instance de type <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c5830-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5830-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5830-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5830-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5830-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="c5830-107">[in] Un paramètre optionnel utilisé pour donner un nom convivial au domaine.</span><span class="sxs-lookup"><span data-stu-id="c5830-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="c5830-108">Ce nom convivial peut être affiché dans les interfaces utilisateur telles que les débogueurs pour identifier le domaine.</span><span class="sxs-lookup"><span data-stu-id="c5830-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="c5830-109">[in] Tableau facultatif de pointeurs vers `IIdentity` instances qui représentent la preuve mappée via la stratégie de sécurité pour établir un jeu d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="c5830-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="c5830-110">Un `IIdentity` objet peut être obtenu en appelant le [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="c5830-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="c5830-111">[out] Un pointeur d’interface de type <xref:System._AppDomain> à une instance de <xref:System.AppDomain?displayProperty=nameWithType> qui peut être utilisé pour contrôler davantage le domaine.</span><span class="sxs-lookup"><span data-stu-id="c5830-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5830-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c5830-112">Return Value</span></span>  
  
|<span data-ttu-id="c5830-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5830-113">HRESULT</span></span>|<span data-ttu-id="c5830-114">Description</span><span class="sxs-lookup"><span data-stu-id="c5830-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5830-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5830-115">S_OK</span></span>|<span data-ttu-id="c5830-116">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="c5830-116">The operation was successful.</span></span>|  
|<span data-ttu-id="c5830-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c5830-117">S_FALSE</span></span>|<span data-ttu-id="c5830-118">L’opération a échoué.</span><span class="sxs-lookup"><span data-stu-id="c5830-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="c5830-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c5830-119">E_FAIL</span></span>|<span data-ttu-id="c5830-120">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c5830-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="c5830-121">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="c5830-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="c5830-122">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c5830-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c5830-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c5830-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c5830-124">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="c5830-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5830-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c5830-125">Requirements</span></span>  
 <span data-ttu-id="c5830-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5830-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5830-127">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5830-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5830-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5830-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5830-129">**Versions du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="c5830-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5830-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5830-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="c5830-131">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="c5830-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
