---
title: ICorRuntimeHost::Start, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
ms.openlocfilehash: bc647ad025b5e22187b476383ed0128761cb632f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721034"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="9bd07-102">ICorRuntimeHost::Start, méthode</span><span class="sxs-lookup"><span data-stu-id="9bd07-102">ICorRuntimeHost::Start Method</span></span>

<span data-ttu-id="9bd07-103">Démarre le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9bd07-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bd07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bd07-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9bd07-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9bd07-105">Return Value</span></span>  
  
|<span data-ttu-id="9bd07-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9bd07-106">HRESULT</span></span>|<span data-ttu-id="9bd07-107">Description</span><span class="sxs-lookup"><span data-stu-id="9bd07-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9bd07-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9bd07-108">S_OK</span></span>|<span data-ttu-id="9bd07-109">L'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="9bd07-109">The operation was successful.</span></span>|  
|<span data-ttu-id="9bd07-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9bd07-110">S_FALSE</span></span>|<span data-ttu-id="9bd07-111">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="9bd07-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9bd07-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9bd07-112">E_FAIL</span></span>|<span data-ttu-id="9bd07-113">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9bd07-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9bd07-114">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9bd07-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="9bd07-115">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9bd07-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9bd07-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9bd07-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9bd07-117">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="9bd07-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bd07-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="9bd07-118">Remarks</span></span>  

 <span data-ttu-id="9bd07-119">En général, il n’est pas nécessaire d’appeler la `Start` méthode, car le CLR démarre automatiquement lors de la première demande d’exécution du code managé.</span><span class="sxs-lookup"><span data-stu-id="9bd07-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bd07-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9bd07-120">Requirements</span></span>  

 <span data-ttu-id="9bd07-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bd07-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bd07-122">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9bd07-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9bd07-123">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9bd07-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9bd07-124">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="9bd07-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd07-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9bd07-125">See also</span></span>

- [<span data-ttu-id="9bd07-126">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="9bd07-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
