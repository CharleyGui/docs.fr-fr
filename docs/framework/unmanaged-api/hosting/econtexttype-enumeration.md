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
ms.openlocfilehash: c6d1ace12bd07fa1f14c8570eca1f950a5c22be9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686330"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="74593-102">EContextType, énumération</span><span class="sxs-lookup"><span data-stu-id="74593-102">EContextType Enumeration</span></span>

<span data-ttu-id="74593-103">Décrit le contexte de sécurité du thread en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="74593-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74593-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74593-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="74593-105">Membres</span><span class="sxs-lookup"><span data-stu-id="74593-105">Members</span></span>  
  
|<span data-ttu-id="74593-106">Membre</span><span class="sxs-lookup"><span data-stu-id="74593-106">Member</span></span>|<span data-ttu-id="74593-107">Description</span><span class="sxs-lookup"><span data-stu-id="74593-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="74593-108">Indique le contexte sur le thread actuel au moment où le common language runtime (CLR) appelle la méthode [IHostSecurityManager :: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) , ou le contexte demandé par le CLR dans un appel à la méthode [IHostSecurityManager :: SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="74593-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="74593-109">Indique un contexte sur lequel l’hôte a des privilèges inférieurs, tels que le garbage collector ou des constructeurs de classe ou de module.</span><span class="sxs-lookup"><span data-stu-id="74593-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74593-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="74593-110">Remarks</span></span>  

 <span data-ttu-id="74593-111">Le CLR fournit l’une des `EContextType` valeurs en tant que valeur de paramètre dans les appels aux `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` méthodes et.</span><span class="sxs-lookup"><span data-stu-id="74593-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74593-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="74593-112">Requirements</span></span>  

 <span data-ttu-id="74593-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74593-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74593-114">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="74593-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="74593-115">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="74593-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="74593-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74593-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74593-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74593-117">See also</span></span>

- [<span data-ttu-id="74593-118">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="74593-118">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="74593-119">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="74593-119">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="74593-120">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="74593-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
