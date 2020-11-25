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
ms.openlocfilehash: c495ce47b699d2e32d1f02e4afcf0444a9930c34
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723907"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="b470e-102">ICorRuntimeHost::CreateDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="b470e-102">ICorRuntimeHost::CreateDomain Method</span></span>

<span data-ttu-id="b470e-103">Crée un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="b470e-103">Creates an application domain.</span></span> <span data-ttu-id="b470e-104">L’appelant reçoit un pointeur d’interface de type <xref:System._AppDomain> vers une instance de type <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b470e-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b470e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b470e-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b470e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b470e-106">Parameters</span></span>  

 `pwzFriendlyName`  
 <span data-ttu-id="b470e-107">dans Paramètre facultatif utilisé pour attribuer un nom convivial au domaine.</span><span class="sxs-lookup"><span data-stu-id="b470e-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="b470e-108">Ce nom convivial peut être affiché dans les interfaces utilisateur, telles que les débogueurs, pour identifier le domaine.</span><span class="sxs-lookup"><span data-stu-id="b470e-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="b470e-109">dans Tableau facultatif de pointeurs vers des `IIdentity` instances qui représentent une preuve mappée par le biais d’une stratégie de sécurité pour établir un jeu d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="b470e-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="b470e-110">Un `IIdentity` objet peut être obtenu en appelant la méthode [CreateEvidence,](icorruntimehost-createevidence-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b470e-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="b470e-111">à Pointeur d’interface de type <xref:System._AppDomain> vers une instance de <xref:System.AppDomain?displayProperty=nameWithType> qui peut être utilisée pour mieux contrôler le domaine.</span><span class="sxs-lookup"><span data-stu-id="b470e-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b470e-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="b470e-112">Return Value</span></span>  
  
|<span data-ttu-id="b470e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b470e-113">HRESULT</span></span>|<span data-ttu-id="b470e-114">Description</span><span class="sxs-lookup"><span data-stu-id="b470e-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b470e-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="b470e-115">S_OK</span></span>|<span data-ttu-id="b470e-116">L'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="b470e-116">The operation was successful.</span></span>|  
|<span data-ttu-id="b470e-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b470e-117">S_FALSE</span></span>|<span data-ttu-id="b470e-118">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="b470e-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="b470e-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b470e-119">E_FAIL</span></span>|<span data-ttu-id="b470e-120">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b470e-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="b470e-121">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b470e-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="b470e-122">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b470e-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b470e-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b470e-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b470e-124">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="b470e-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b470e-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b470e-125">Requirements</span></span>  

 <span data-ttu-id="b470e-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b470e-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b470e-127">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b470e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b470e-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b470e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b470e-129">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="b470e-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b470e-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b470e-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="b470e-131">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="b470e-131">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
