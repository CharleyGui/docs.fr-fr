---
title: EContextType, énumération
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
ms.openlocfilehash: 5e82f542bdc364a52fc558e582134a7d8d554ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131145"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="7cd86-102">EContextType, énumération</span><span class="sxs-lookup"><span data-stu-id="7cd86-102">EContextType Enumeration</span></span>
<span data-ttu-id="7cd86-103">Décrit le contexte de sécurité du thread en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7cd86-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cd86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cd86-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="7cd86-105">Membres</span><span class="sxs-lookup"><span data-stu-id="7cd86-105">Members</span></span>  
  
|<span data-ttu-id="7cd86-106">Membre</span><span class="sxs-lookup"><span data-stu-id="7cd86-106">Member</span></span>|<span data-ttu-id="7cd86-107">Description</span><span class="sxs-lookup"><span data-stu-id="7cd86-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="7cd86-108">Indique le contexte sur le thread actuel au moment où le common language runtime (CLR) appelle la méthode [IHostSecurityManager :: GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) , ou le contexte demandé par le CLR dans un appel à [IHostSecurityManager :: SetSecurityContext ](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)méthode.</span><span class="sxs-lookup"><span data-stu-id="7cd86-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="7cd86-109">Indique un contexte sur lequel l’hôte a des privilèges inférieurs, tels que le garbage collector ou des constructeurs de classe ou de module.</span><span class="sxs-lookup"><span data-stu-id="7cd86-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cd86-110">Notes</span><span class="sxs-lookup"><span data-stu-id="7cd86-110">Remarks</span></span>  
 <span data-ttu-id="7cd86-111">Le CLR fournit l’une des valeurs `EContextType` en tant que valeur de paramètre dans les appels aux méthodes `IHostSecurityManager::GetSecurityContext` et `IHostSecurityManager::SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="7cd86-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cd86-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="7cd86-112">Requirements</span></span>  
 <span data-ttu-id="7cd86-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cd86-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cd86-114">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7cd86-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7cd86-115">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7cd86-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7cd86-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cd86-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cd86-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cd86-117">See also</span></span>

- [<span data-ttu-id="7cd86-118">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="7cd86-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="7cd86-119">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="7cd86-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="7cd86-120">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="7cd86-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
