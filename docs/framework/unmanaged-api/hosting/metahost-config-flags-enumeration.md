---
title: METAHOST_CONFIG_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- METAHOST_CONFIG_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_CONFIG_FLAGS
helpviewer_keywords:
- METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type:
- apiref
ms.openlocfilehash: 01e55659bf2a348ec763f51112cbdcd706f27c84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730004"
---
# <a name="metahost_config_flags-enumeration"></a>METAHOST_CONFIG_FLAGS, énumération

Décrit les indicateurs possibles retournés dans le `pdwConfigFlags` paramètre de la méthode [ICLRMetaHostPolicy :: GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) , indiquant la présence et le paramétrage de l' `useLegacyV2RuntimeActivationPolicy` attribut dans l' [ \<startup> élément](../../configure-apps/file-schema/startup/startup-element.md) du fichier de configuration.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|L' `useLegacyV2RuntimeActivationPolicy` attribut n’était pas présent dans l' [ \<startup> élément](../../configure-apps/file-schema/startup/startup-element.md).|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|L' `useLegacyV2RuntimeActivationPolicy` attribut était présent et a la valeur `true` .|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|L' `useLegacyV2RuntimeActivationPolicy` attribut était présent et a la valeur `false` .|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|Appliquez ce masque à la valeur retournée dans `pdwConfigFlags` pour récupérer les valeurs correspondant à `useLegacyV2RuntimeActivationPolicy` .|  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations d'hébergement](hosting-enumerations.md)
- [GetRequestedRuntime, méthode](iclrmetahostpolicy-getrequestedruntime-method.md)
- [\<startup> Appartient](../../configure-apps/file-schema/startup/startup-element.md)
