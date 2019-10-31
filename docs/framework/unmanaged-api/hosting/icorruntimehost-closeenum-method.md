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
ms.openlocfilehash: e2eddfab68e5c9e2ebffe2c96c9348f3cd799c7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127749"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="60257-102">ICorRuntimeHost::CloseEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="60257-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="60257-103">Réinitialise un énumérateur de domaine au début de la liste de domaines.</span><span class="sxs-lookup"><span data-stu-id="60257-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60257-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60257-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60257-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="60257-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="60257-106">dans Énumérateur à réinitialiser.</span><span class="sxs-lookup"><span data-stu-id="60257-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60257-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="60257-107">Return Value</span></span>  
  
|<span data-ttu-id="60257-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60257-108">HRESULT</span></span>|<span data-ttu-id="60257-109">Description</span><span class="sxs-lookup"><span data-stu-id="60257-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60257-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="60257-110">S_OK</span></span>|<span data-ttu-id="60257-111">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="60257-111">The operation was successful.</span></span>|  
|<span data-ttu-id="60257-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="60257-112">S_FALSE</span></span>|<span data-ttu-id="60257-113">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="60257-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="60257-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="60257-114">E_FAIL</span></span>|<span data-ttu-id="60257-115">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="60257-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="60257-116">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="60257-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="60257-117">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="60257-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="60257-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="60257-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="60257-119">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="60257-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60257-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="60257-120">Requirements</span></span>  
 <span data-ttu-id="60257-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60257-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60257-122">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="60257-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60257-123">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="60257-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60257-124">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="60257-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60257-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60257-125">See also</span></span>

- [<span data-ttu-id="60257-126">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="60257-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="60257-127">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="60257-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
