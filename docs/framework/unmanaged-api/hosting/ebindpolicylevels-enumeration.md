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
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels, énumération
Fournit des indicateurs pour spécifier le niveau auquel appliquer ou modifier la stratégie d’assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|Spécifie que la stratégie doit être appliquée au niveau de l’administrateur.|  
|`ePolicyLevelApp`|Spécifie que la stratégie doit être appliquée au niveau de l’application.|  
|`ePolicyLevelHost`|Spécifie que la stratégie doit être appliquée au niveau de l’hôte.|  
|`ePolicyLevelNone`|Ne spécifie aucun indicateur de niveau stratégie.|  
|`ePolicyLevelPublisher`|Spécifie que la stratégie doit être appliquée au niveau du serveur de publication.|  
|`ePolicyLevelRetargetable`|Spécifie que la stratégie doit être applicable à des niveaux variables.|  
|`ePolicyPortability`|Spécifie que la stratégie doit prendre en charge la portabilité entre les implémentations d’un assembly .NET Framework. Consultez l’élément [\<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) fichier de configuration.|  
|`ePolicyUnifiedToCLR`|Spécifie que la stratégie doit être unifiée à celle de la common language runtime (CLR).|  
  
## <a name="remarks"></a>Notes  
 Cette énumération est passée aux méthodes de l’interface [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) pour spécifier les modifications apportées à la stratégie d’application.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRAssemblyIdentityManager, interface](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
