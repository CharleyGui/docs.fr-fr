---
title: ICorRuntimeHost::NextDomain, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
ms.openlocfilehash: 36eacedfb83c1248fc252091872bcfeecdbcd874
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139516"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="53e53-102">ICorRuntimeHost::NextDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="53e53-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="53e53-103">Obtient un pointeur d’interface vers le domaine suivant dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="53e53-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53e53-104">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53e53-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="53e53-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="53e53-106">dans Énumérateur obtenu via un appel à [EnumDomains,](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="53e53-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="53e53-107">à Pointeur d’interface vers le type de <xref:System._AppDomain?displayProperty=nameWithType> qui représente le domaine suivant dans l’énumération, ou null, s’il n’existe plus de domaines.</span><span class="sxs-lookup"><span data-stu-id="53e53-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53e53-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="53e53-108">Return Value</span></span>  
  
|<span data-ttu-id="53e53-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53e53-109">HRESULT</span></span>|<span data-ttu-id="53e53-110">Description</span><span class="sxs-lookup"><span data-stu-id="53e53-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53e53-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="53e53-111">S_OK</span></span>|<span data-ttu-id="53e53-112">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="53e53-112">The operation was successful.</span></span>|  
|<span data-ttu-id="53e53-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="53e53-113">S_FALSE</span></span>|<span data-ttu-id="53e53-114">L’opération n’a pas pu se terminer ou il n’y a plus de domaines dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="53e53-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="53e53-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="53e53-115">E_FAIL</span></span>|<span data-ttu-id="53e53-116">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="53e53-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="53e53-117">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="53e53-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="53e53-118">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="53e53-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="53e53-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="53e53-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="53e53-120">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="53e53-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="53e53-121">spécifications</span><span class="sxs-lookup"><span data-stu-id="53e53-121">Requirements</span></span>  
 <span data-ttu-id="53e53-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53e53-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53e53-123">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="53e53-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53e53-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="53e53-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53e53-125">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="53e53-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e53-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53e53-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="53e53-127">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="53e53-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
