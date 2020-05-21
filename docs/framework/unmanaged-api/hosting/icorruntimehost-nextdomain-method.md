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
ms.openlocfilehash: 079164d15141983711e976e0209cc22c818d9cd9
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760418"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="49e8a-102">ICorRuntimeHost::NextDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="49e8a-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="49e8a-103">Obtient un pointeur d’interface vers le domaine suivant dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="49e8a-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49e8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49e8a-104">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49e8a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49e8a-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="49e8a-106">dans Énumérateur obtenu via un appel à [EnumDomains,](icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="49e8a-106">[in] The enumerator that was obtained through a call to [EnumDomains](icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="49e8a-107">à Pointeur d’interface vers le <xref:System._AppDomain?displayProperty=nameWithType> type qui représente le domaine suivant dans l’énumération, ou null, s’il n’existe plus de domaines.</span><span class="sxs-lookup"><span data-stu-id="49e8a-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49e8a-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="49e8a-108">Return Value</span></span>  
  
|<span data-ttu-id="49e8a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49e8a-109">HRESULT</span></span>|<span data-ttu-id="49e8a-110">Description</span><span class="sxs-lookup"><span data-stu-id="49e8a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49e8a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="49e8a-111">S_OK</span></span>|<span data-ttu-id="49e8a-112">L'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="49e8a-112">The operation was successful.</span></span>|  
|<span data-ttu-id="49e8a-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="49e8a-113">S_FALSE</span></span>|<span data-ttu-id="49e8a-114">L’opération n’a pas pu se terminer ou il n’y a plus de domaines dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="49e8a-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="49e8a-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="49e8a-115">E_FAIL</span></span>|<span data-ttu-id="49e8a-116">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="49e8a-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="49e8a-117">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="49e8a-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="49e8a-118">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="49e8a-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="49e8a-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="49e8a-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="49e8a-120">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="49e8a-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49e8a-121">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="49e8a-121">Requirements</span></span>  
 <span data-ttu-id="49e8a-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49e8a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49e8a-123">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="49e8a-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49e8a-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="49e8a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49e8a-125">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="49e8a-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49e8a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49e8a-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="49e8a-127">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="49e8a-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
