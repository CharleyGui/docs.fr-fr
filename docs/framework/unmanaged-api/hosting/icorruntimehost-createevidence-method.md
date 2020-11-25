---
title: ICorRuntimeHost::CreateEvidence, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
ms.openlocfilehash: 6627fce519934177aefd26a612e5b00ca1941d02
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715665"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="5100f-102">ICorRuntimeHost::CreateEvidence, méthode</span><span class="sxs-lookup"><span data-stu-id="5100f-102">ICorRuntimeHost::CreateEvidence Method</span></span>

<span data-ttu-id="5100f-103">Obtient un pointeur d’interface de type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> , qui permet à l’hôte de créer une preuve de sécurité à passer à la méthode [CreateDomain](icorruntimehost-createdomain-method.md) ou [CreateDomainEx](icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5100f-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5100f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5100f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5100f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5100f-105">Parameters</span></span>  

 `pEvidence`  
 <span data-ttu-id="5100f-106">à Pointeur d’interface vers une <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance utilisée pour créer la preuve de sécurité.</span><span class="sxs-lookup"><span data-stu-id="5100f-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="5100f-107">Ce pointeur étant typé `IUnknown` , les appelants doivent généralement appeler `QueryInterface` sur cette interface pour obtenir un pointeur vers un <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5100f-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5100f-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="5100f-108">Return Value</span></span>  
  
|<span data-ttu-id="5100f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5100f-109">HRESULT</span></span>|<span data-ttu-id="5100f-110">Description</span><span class="sxs-lookup"><span data-stu-id="5100f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5100f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5100f-111">S_OK</span></span>|<span data-ttu-id="5100f-112">L'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="5100f-112">The operation was successful.</span></span>|  
|<span data-ttu-id="5100f-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5100f-113">S_FALSE</span></span>|<span data-ttu-id="5100f-114">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="5100f-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="5100f-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5100f-115">E_FAIL</span></span>|<span data-ttu-id="5100f-116">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="5100f-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="5100f-117">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="5100f-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="5100f-118">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5100f-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5100f-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5100f-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5100f-120">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="5100f-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5100f-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="5100f-121">Remarks</span></span>  

 <span data-ttu-id="5100f-122">Cette méthode retourne une collection vide qui ne peut pas être remplie à partir du code natif.</span><span class="sxs-lookup"><span data-stu-id="5100f-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="5100f-123">Vous devez utiliser la <xref:System.Security.Policy.Evidence> méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="5100f-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5100f-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5100f-124">Requirements</span></span>  

 <span data-ttu-id="5100f-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5100f-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5100f-126">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5100f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5100f-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5100f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5100f-128">**Version de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="5100f-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5100f-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5100f-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="5100f-130">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="5100f-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
