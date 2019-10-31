---
title: EInitializeNewDomainFlags, énumération
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
ms.openlocfilehash: 3693285e13d0650f7662e2187471027cc4c40704
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129419"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="e87db-102">EInitializeNewDomainFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="e87db-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="e87db-103">Permet à l’hôte de fournir au runtime des informations sur l’initialisation d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="e87db-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e87db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e87db-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="e87db-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e87db-105">Members</span></span>  
  
|<span data-ttu-id="e87db-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e87db-106">Member</span></span>|<span data-ttu-id="e87db-107">Description</span><span class="sxs-lookup"><span data-stu-id="e87db-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="e87db-108">Aucun indicateur.</span><span class="sxs-lookup"><span data-stu-id="e87db-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="e87db-109">Informe le common language runtime (CLR) que l’hôte n’apporte pas de modifications à l’état de sécurité du domaine d’application dans la méthode <xref:System.AppDomainManager.InitializeNewDomain%2A>.</span><span class="sxs-lookup"><span data-stu-id="e87db-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e87db-110">Notes</span><span class="sxs-lookup"><span data-stu-id="e87db-110">Remarks</span></span>  
 <span data-ttu-id="e87db-111">La méthode [ICLRDomainManager :: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) prend un paramètre de type `EInitializeNewDomainFlags`.</span><span class="sxs-lookup"><span data-stu-id="e87db-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e87db-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="e87db-112">Requirements</span></span>  
 <span data-ttu-id="e87db-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e87db-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e87db-114">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e87db-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e87db-115">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e87db-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e87db-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e87db-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e87db-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e87db-117">See also</span></span>

- [<span data-ttu-id="e87db-118">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="e87db-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="e87db-119">SetAppDomainManagerType, méthode</span><span class="sxs-lookup"><span data-stu-id="e87db-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
