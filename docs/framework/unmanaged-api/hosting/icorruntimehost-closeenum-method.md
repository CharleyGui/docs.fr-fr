---
title: ICorRuntimeHost::CloseEnum, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bfddd1d8f6fed105224cb2294d68f3f0bc016403
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762152"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="76e1b-102">ICorRuntimeHost::CloseEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="76e1b-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="76e1b-103">Réinitialise un énumérateur de domaine au début de la liste des domaines.</span><span class="sxs-lookup"><span data-stu-id="76e1b-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76e1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76e1b-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76e1b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="76e1b-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="76e1b-106">[in] L’énumérateur à réinitialiser.</span><span class="sxs-lookup"><span data-stu-id="76e1b-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76e1b-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="76e1b-107">Return Value</span></span>  
  
|<span data-ttu-id="76e1b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76e1b-108">HRESULT</span></span>|<span data-ttu-id="76e1b-109">Description</span><span class="sxs-lookup"><span data-stu-id="76e1b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76e1b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="76e1b-110">S_OK</span></span>|<span data-ttu-id="76e1b-111">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="76e1b-111">The operation was successful.</span></span>|  
|<span data-ttu-id="76e1b-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="76e1b-112">S_FALSE</span></span>|<span data-ttu-id="76e1b-113">L’opération a échoué.</span><span class="sxs-lookup"><span data-stu-id="76e1b-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="76e1b-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="76e1b-114">E_FAIL</span></span>|<span data-ttu-id="76e1b-115">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="76e1b-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="76e1b-116">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="76e1b-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="76e1b-117">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="76e1b-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="76e1b-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="76e1b-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="76e1b-119">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="76e1b-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="76e1b-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="76e1b-120">Requirements</span></span>  
 <span data-ttu-id="76e1b-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76e1b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76e1b-122">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="76e1b-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="76e1b-123">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="76e1b-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="76e1b-124">**Versions du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="76e1b-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76e1b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76e1b-125">See also</span></span>

- [<span data-ttu-id="76e1b-126">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="76e1b-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="76e1b-127">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="76e1b-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
