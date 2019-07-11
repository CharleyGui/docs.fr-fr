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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe80050d7b513bce2660b81c5e4faa35b375f22b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780033"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="09449-102">ICorRuntimeHost::GetDefaultDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="09449-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="09449-103">Obtient un pointeur d’interface de type <xref:System._AppDomain?displayProperty=nameWithType> qui représente le domaine par défaut pour le processus actuel.</span><span class="sxs-lookup"><span data-stu-id="09449-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09449-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09449-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09449-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="09449-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="09449-106">[out] Un pointeur d’interface de type <xref:System._AppDomain?displayProperty=nameWithType> à la <xref:System.AppDomain> instance qui représente le domaine d’application par défaut pour le processus.</span><span class="sxs-lookup"><span data-stu-id="09449-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="09449-107">Ce pointeur est tapé `IUnknown`, de sorte que les appelants doivent généralement appeler `QueryInterface` pour obtenir un pointeur d’interface de type <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09449-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09449-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="09449-108">Return Value</span></span>  
  
|<span data-ttu-id="09449-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09449-109">HRESULT</span></span>|<span data-ttu-id="09449-110">Description</span><span class="sxs-lookup"><span data-stu-id="09449-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09449-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="09449-111">S_OK</span></span>|<span data-ttu-id="09449-112">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="09449-112">The operation was successful.</span></span>|  
|<span data-ttu-id="09449-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="09449-113">S_FALSE</span></span>|<span data-ttu-id="09449-114">L’opération a échoué.</span><span class="sxs-lookup"><span data-stu-id="09449-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="09449-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="09449-115">E_FAIL</span></span>|<span data-ttu-id="09449-116">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="09449-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="09449-117">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="09449-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="09449-118">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="09449-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="09449-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="09449-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="09449-120">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="09449-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09449-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="09449-121">Requirements</span></span>  
 <span data-ttu-id="09449-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09449-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09449-123">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="09449-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09449-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="09449-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09449-125">**Versions du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="09449-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09449-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09449-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="09449-127">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="09449-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
