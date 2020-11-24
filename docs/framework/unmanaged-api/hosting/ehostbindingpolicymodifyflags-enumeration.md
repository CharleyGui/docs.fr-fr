---
title: EHostBindingPolicyModifyFlags, énumération
ms.date: 03/30/2017
api_name:
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
ms.openlocfilehash: ec64f9bec0ee9b63796958b17c7f10b87692f1d0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686142"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="604b2-102">EHostBindingPolicyModifyFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="604b2-102">EHostBindingPolicyModifyFlags Enumeration</span></span>

<span data-ttu-id="604b2-103">Permet à l’hôte de spécifier le type de redirection que le common language runtime (CLR) doit effectuer lors de l’application des modifications de stratégie d’un assembly source à un assembly cible.</span><span class="sxs-lookup"><span data-stu-id="604b2-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="604b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="604b2-104">Syntax</span></span>  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="604b2-105">Membres</span><span class="sxs-lookup"><span data-stu-id="604b2-105">Members</span></span>  
  
|<span data-ttu-id="604b2-106">Membre</span><span class="sxs-lookup"><span data-stu-id="604b2-106">Member</span></span>|<span data-ttu-id="604b2-107">Description</span><span class="sxs-lookup"><span data-stu-id="604b2-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="604b2-108">Spécifie que le CLR doit chaîner les valeurs de stratégie de l’assembly source sur celles de l’assembly cible.</span><span class="sxs-lookup"><span data-stu-id="604b2-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="604b2-109">Spécifie que le CLR effectuera l’action par défaut.</span><span class="sxs-lookup"><span data-stu-id="604b2-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="604b2-110">Spécifie que le CLR définit les valeurs de stratégie de l’assembly cible sur les valeurs maximales.</span><span class="sxs-lookup"><span data-stu-id="604b2-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="604b2-111">Spécifie que le CLR va remplacer les valeurs de stratégie de l’assembly cible par celles de l’assembly source.</span><span class="sxs-lookup"><span data-stu-id="604b2-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="604b2-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="604b2-112">Remarks</span></span>  

 <span data-ttu-id="604b2-113">La méthode [ICLRHostBindingPolicyManager :: ModifyApplicationPolicy,](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) prend un paramètre de type `EHostBindingPolicyModifyFlags` .</span><span class="sxs-lookup"><span data-stu-id="604b2-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="604b2-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="604b2-114">Requirements</span></span>  

 <span data-ttu-id="604b2-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="604b2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="604b2-116">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="604b2-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="604b2-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="604b2-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="604b2-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="604b2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="604b2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="604b2-119">See also</span></span>

- [<span data-ttu-id="604b2-120">ICLRHostBindingPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="604b2-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="604b2-121">Énumérations d'hébergement</span><span class="sxs-lookup"><span data-stu-id="604b2-121">Hosting Enumerations</span></span>](hosting-enumerations.md)
