---
title: ICLRDebugManager::SetSymbolReadingPolicy, méthode
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetSymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type:
- apiref
ms.openlocfilehash: a311166e79f930e763b0338451f6356c8c93f929
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670136"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="9ca05-102">ICLRDebugManager::SetSymbolReadingPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="9ca05-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>

<span data-ttu-id="9ca05-103">Définit la stratégie de lecture des fichiers de base de données du programme (PDB).</span><span class="sxs-lookup"><span data-stu-id="9ca05-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="9ca05-104">La stratégie détermine si les informations sur les numéros de ligne et les fichiers sont incluses dans les piles des appels.</span><span class="sxs-lookup"><span data-stu-id="9ca05-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca05-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ca05-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ca05-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9ca05-106">Parameters</span></span>  

 `policy`  
 <span data-ttu-id="9ca05-107">dans Membre de l’énumération [ESymbolReadingPolicy,](esymbolreadingpolicy-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="9ca05-107">[in] A member of the [ESymbolReadingPolicy](esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ca05-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9ca05-108">Return Value</span></span>  
  
|<span data-ttu-id="9ca05-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ca05-109">HRESULT</span></span>|<span data-ttu-id="9ca05-110">Description</span><span class="sxs-lookup"><span data-stu-id="9ca05-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ca05-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ca05-111">S_OK</span></span>|<span data-ttu-id="9ca05-112">`SetSymbolReadingPolicy` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9ca05-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="9ca05-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9ca05-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9ca05-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="9ca05-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9ca05-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9ca05-115">E_FAIL</span></span>|<span data-ttu-id="9ca05-116">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9ca05-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9ca05-117">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9ca05-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9ca05-118">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9ca05-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ca05-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9ca05-119">Requirements</span></span>  

 <span data-ttu-id="9ca05-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ca05-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ca05-121">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9ca05-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ca05-122">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ca05-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ca05-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ca05-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca05-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ca05-124">See also</span></span>

- [<span data-ttu-id="9ca05-125">ICLRDebugManager, interface</span><span class="sxs-lookup"><span data-stu-id="9ca05-125">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
