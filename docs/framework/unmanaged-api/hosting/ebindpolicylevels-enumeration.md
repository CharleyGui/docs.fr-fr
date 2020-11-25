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
ms.openlocfilehash: a0992ca8ac4bfffef681c74de455a0eeb627a042
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726845"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="6cfd2-102">EBindPolicyLevels, énumération</span><span class="sxs-lookup"><span data-stu-id="6cfd2-102">EBindPolicyLevels Enumeration</span></span>

<span data-ttu-id="6cfd2-103">Fournit des indicateurs pour spécifier le niveau auquel appliquer ou modifier la stratégie d’assembly.</span><span class="sxs-lookup"><span data-stu-id="6cfd2-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cfd2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cfd2-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6cfd2-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6cfd2-105">Members</span></span>  
  
|<span data-ttu-id="6cfd2-106">Membre</span><span class="sxs-lookup"><span data-stu-id="6cfd2-106">Member</span></span>|<span data-ttu-id="6cfd2-107">Description</span><span class="sxs-lookup"><span data-stu-id="6cfd2-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="6cfd2-108">Spécifie que la stratégie doit être appliquée au niveau de l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="6cfd2-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="6cfd2-109">Spécifie que la stratégie doit être appliquée au niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="6cfd2-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="6cfd2-110">Spécifie que la stratégie doit être appliquée au niveau de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="6cfd2-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="6cfd2-111">Ne spécifie aucun indicateur de niveau stratégie.</span><span class="sxs-lookup"><span data-stu-id="6cfd2-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="6cfd2-112">Spécifie que la stratégie doit être appliquée au niveau du serveur de publication.</span><span class="sxs-lookup"><span data-stu-id="6cfd2-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="6cfd2-113">Spécifie que la stratégie doit être applicable à des niveaux variables.</span><span class="sxs-lookup"><span data-stu-id="6cfd2-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="6cfd2-114">Spécifie que la stratégie doit prendre en charge la portabilité entre les implémentations d’un assembly .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6cfd2-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="6cfd2-115">Consultez l' [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) élément fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="6cfd2-115">See the [\<supportPortability>](../../configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="6cfd2-116">Spécifie que la stratégie doit être unifiée à celle de la common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6cfd2-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cfd2-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="6cfd2-117">Remarks</span></span>  

 <span data-ttu-id="6cfd2-118">Cette énumération est passée aux méthodes de l’interface [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) pour spécifier les modifications apportées à la stratégie d’application.</span><span class="sxs-lookup"><span data-stu-id="6cfd2-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cfd2-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6cfd2-119">Requirements</span></span>  

 <span data-ttu-id="6cfd2-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cfd2-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cfd2-121">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6cfd2-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cfd2-122">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6cfd2-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cfd2-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cfd2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cfd2-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cfd2-124">See also</span></span>

- [<span data-ttu-id="6cfd2-125">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="6cfd2-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="6cfd2-126">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="6cfd2-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
