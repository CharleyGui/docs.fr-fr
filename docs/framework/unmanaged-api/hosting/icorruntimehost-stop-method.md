---
title: ICorRuntimeHost::Stop, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
ms.openlocfilehash: 4117c1297f02032fda80520a7709833217ec94b1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762693"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="371c9-102">ICorRuntimeHost::Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="371c9-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="371c9-103">Arrête l’exécution du code dans le runtime pour le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="371c9-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="371c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="371c9-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="371c9-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="371c9-105">Return Value</span></span>  
  
|<span data-ttu-id="371c9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="371c9-106">HRESULT</span></span>|<span data-ttu-id="371c9-107">Description</span><span class="sxs-lookup"><span data-stu-id="371c9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="371c9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="371c9-108">S_OK</span></span>|<span data-ttu-id="371c9-109">L'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="371c9-109">The operation was successful.</span></span>|  
|<span data-ttu-id="371c9-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="371c9-110">S_FALSE</span></span>|<span data-ttu-id="371c9-111">L’opération n’a pas pu se terminer.</span><span class="sxs-lookup"><span data-stu-id="371c9-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="371c9-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="371c9-112">E_FAIL</span></span>|<span data-ttu-id="371c9-113">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="371c9-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="371c9-114">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="371c9-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="371c9-115">Les appels suivants à des API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="371c9-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="371c9-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="371c9-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="371c9-117">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="371c9-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="371c9-118">Notes</span><span class="sxs-lookup"><span data-stu-id="371c9-118">Remarks</span></span>  
 <span data-ttu-id="371c9-119">Il n’est généralement pas nécessaire d’appeler la `Stop` méthode, car le code cesse de s’exécuter lorsque le processus se termine.</span><span class="sxs-lookup"><span data-stu-id="371c9-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="371c9-120">Après un appel à `Stop` , le CLR ne peut pas être réinitialisé dans le même processus.</span><span class="sxs-lookup"><span data-stu-id="371c9-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="371c9-121">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="371c9-121">Requirements</span></span>  
 <span data-ttu-id="371c9-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="371c9-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="371c9-123">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="371c9-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="371c9-124">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="371c9-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="371c9-125">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="371c9-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="371c9-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="371c9-126">See also</span></span>

- [<span data-ttu-id="371c9-127">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="371c9-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
