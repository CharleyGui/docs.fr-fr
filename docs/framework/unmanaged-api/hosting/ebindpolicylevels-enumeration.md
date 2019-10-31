---
title: EBindPolicyLevels, énumération
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
ms.openlocfilehash: 81aef6beb9ee6d622519738d24fdd0a4d42a75b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136549"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="9b405-102">EBindPolicyLevels, énumération</span><span class="sxs-lookup"><span data-stu-id="9b405-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="9b405-103">Fournit des indicateurs pour spécifier le niveau auquel appliquer ou modifier la stratégie d’assembly.</span><span class="sxs-lookup"><span data-stu-id="9b405-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b405-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b405-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a><span data-ttu-id="9b405-105">Membres</span><span class="sxs-lookup"><span data-stu-id="9b405-105">Members</span></span>  
  
|<span data-ttu-id="9b405-106">Membre</span><span class="sxs-lookup"><span data-stu-id="9b405-106">Member</span></span>|<span data-ttu-id="9b405-107">Description</span><span class="sxs-lookup"><span data-stu-id="9b405-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="9b405-108">Spécifie que la stratégie doit être appliquée au niveau de l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="9b405-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="9b405-109">Spécifie que la stratégie doit être appliquée au niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="9b405-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="9b405-110">Spécifie que la stratégie doit être appliquée au niveau de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="9b405-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="9b405-111">Ne spécifie aucun indicateur de niveau stratégie.</span><span class="sxs-lookup"><span data-stu-id="9b405-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="9b405-112">Spécifie que la stratégie doit être appliquée au niveau du serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="9b405-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="9b405-113">Spécifie que la stratégie doit être applicable à des niveaux variables.</span><span class="sxs-lookup"><span data-stu-id="9b405-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="9b405-114">Spécifie que la stratégie doit prendre en charge la portabilité entre les implémentations d’un assembly .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b405-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="9b405-115">Consultez l’élément [\<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="9b405-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="9b405-116">Spécifie que la stratégie doit être unifiée à celle de la common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9b405-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b405-117">Notes</span><span class="sxs-lookup"><span data-stu-id="9b405-117">Remarks</span></span>  
 <span data-ttu-id="9b405-118">Cette énumération est passée aux méthodes de l’interface [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) pour spécifier les modifications apportées à la stratégie d’application.</span><span class="sxs-lookup"><span data-stu-id="9b405-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b405-119">spécifications</span><span class="sxs-lookup"><span data-stu-id="9b405-119">Requirements</span></span>  
 <span data-ttu-id="9b405-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b405-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b405-121">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9b405-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b405-122">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9b405-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b405-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b405-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b405-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b405-124">See also</span></span>

- [<span data-ttu-id="9b405-125">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="9b405-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="9b405-126">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="9b405-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
