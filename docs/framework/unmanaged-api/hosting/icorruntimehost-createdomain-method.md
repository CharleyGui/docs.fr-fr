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
ms.openlocfilehash: 74f17c77e74edb1226dda2d9ebaa9486e1769ce4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762355"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="32667-102">ICorRuntimeHost::CreateDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="32667-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="32667-103">Crée un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="32667-103">Creates an application domain.</span></span> <span data-ttu-id="32667-104">L’appelant reçoit un pointeur d’interface de type <xref:System._AppDomain> vers une instance de type <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="32667-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32667-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32667-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32667-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="32667-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="32667-107">dans Paramètre facultatif utilisé pour attribuer un nom convivial au domaine.</span><span class="sxs-lookup"><span data-stu-id="32667-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="32667-108">Ce nom convivial peut être affiché dans les interfaces utilisateur, telles que les débogueurs, pour identifier le domaine.</span><span class="sxs-lookup"><span data-stu-id="32667-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="32667-109">dans Tableau facultatif de pointeurs vers des `IIdentity` instances qui représentent une preuve mappée par le biais d’une stratégie de sécurité pour établir un jeu d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="32667-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="32667-110">Un `IIdentity` objet peut être obtenu en appelant la méthode [CreateEvidence,](icorruntimehost-createevidence-method.md) .</span><span class="sxs-lookup"><span data-stu-id="32667-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="32667-111">à Pointeur d’interface de type <xref:System._AppDomain> vers une instance de <xref:System.AppDomain?displayProperty=nameWithType> qui peut être utilisée pour mieux contrôler le domaine.</span><span class="sxs-lookup"><span data-stu-id="32667-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32667-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="32667-112">Return Value</span></span>  
  
|<span data-ttu-id="32667-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32667-113">HRESULT</span></span>|<span data-ttu-id="32667-114">Description</span><span class="sxs-lookup"><span data-stu-id="32667-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32667-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="32667-115">S_OK</span></span>|<span data-ttu-id="32667-116">L'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="32667-116">The operation was successful.</span></span>|  
|<span data-ttu-id="32667-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="32667-117">S_FALSE</span></span>|<span data-ttu-id="32667-118">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="32667-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="32667-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="32667-119">E_FAIL</span></span>|<span data-ttu-id="32667-120">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="32667-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="32667-121">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="32667-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="32667-122">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="32667-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="32667-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="32667-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="32667-124">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="32667-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="32667-125">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="32667-125">Requirements</span></span>  
 <span data-ttu-id="32667-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32667-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32667-127">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="32667-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32667-128">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="32667-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32667-129">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="32667-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32667-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32667-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="32667-131">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="32667-131">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
