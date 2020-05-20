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
ms.openlocfilehash: 256c362ae0aea51fea16ce799db243b105dee81a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616240"
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a>EHostBindingPolicyModifyFlags, énumération
Permet à l’hôte de spécifier le type de redirection que le common language runtime (CLR) doit effectuer lors de l’application des modifications de stratégie d’un assembly source à un assembly cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|Spécifie que le CLR doit chaîner les valeurs de stratégie de l’assembly source sur celles de l’assembly cible.|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|Spécifie que le CLR effectuera l’action par défaut.|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|Spécifie que le CLR définit les valeurs de stratégie de l’assembly cible sur les valeurs maximales.|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|Spécifie que le CLR va remplacer les valeurs de stratégie de l’assembly cible par celles de l’assembly source.|  
  
## <a name="remarks"></a>Notes  
 La méthode [ICLRHostBindingPolicyManager :: ModifyApplicationPolicy,](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) prend un paramètre de type `EHostBindingPolicyModifyFlags` .  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRHostBindingPolicyManager, interface](iclrhostbindingpolicymanager-interface.md)
- [Énumérations d'hébergement](hosting-enumerations.md)
