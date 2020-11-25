---
title: ICorRuntimeHost::GetDefaultDomain, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
ms.openlocfilehash: 673c32c86c808c36db6454b8a9f0d8e68f9b1258
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720631"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="e6932-102">ICorRuntimeHost::GetDefaultDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="e6932-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>

<span data-ttu-id="e6932-103">Obtient un pointeur d’interface de type <xref:System._AppDomain?displayProperty=nameWithType> qui représente le domaine par défaut pour le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="e6932-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6932-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6932-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6932-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e6932-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="e6932-106">à Pointeur d’interface de type <xref:System._AppDomain?displayProperty=nameWithType> vers l' <xref:System.AppDomain> instance de qui représente le domaine d’application par défaut pour le processus.</span><span class="sxs-lookup"><span data-stu-id="e6932-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="e6932-107">Ce pointeur étant typé `IUnknown` , les appelants doivent généralement appeler `QueryInterface` pour obtenir un pointeur d’interface de type <xref:System._AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e6932-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6932-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e6932-108">Return Value</span></span>  
  
|<span data-ttu-id="e6932-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6932-109">HRESULT</span></span>|<span data-ttu-id="e6932-110">Description</span><span class="sxs-lookup"><span data-stu-id="e6932-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6932-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6932-111">S_OK</span></span>|<span data-ttu-id="e6932-112">L'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="e6932-112">The operation was successful.</span></span>|  
|<span data-ttu-id="e6932-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e6932-113">S_FALSE</span></span>|<span data-ttu-id="e6932-114">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="e6932-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e6932-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e6932-115">E_FAIL</span></span>|<span data-ttu-id="e6932-116">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e6932-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e6932-117">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e6932-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e6932-118">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e6932-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e6932-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e6932-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e6932-120">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="e6932-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6932-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e6932-121">Requirements</span></span>  

 <span data-ttu-id="e6932-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6932-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6932-123">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e6932-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6932-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e6932-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6932-125">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="e6932-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6932-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6932-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="e6932-127">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="e6932-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
