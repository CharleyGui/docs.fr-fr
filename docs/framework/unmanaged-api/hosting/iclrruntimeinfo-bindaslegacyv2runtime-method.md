---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
ms.openlocfilehash: f0a03ecce49bbc3c1c03d037c9be31a8e994259d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732089"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime, méthode

Lie le runtime actuel pour toutes les décisions de stratégie d’activation d’common language runtime (CLR) version 2 héritées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>Valeur de retour  

 Cette méthode retourne les HRESULT spécifiques suivants :  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La liaison a réussi, ou ce Runtime était déjà lié en tant que Runtime de la stratégie d’activation CLR version 2 héritée.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Un Runtime différent était déjà lié à la stratégie d’activation héritée du CLR version 2.|  
  
## <a name="remarks"></a>Remarques  

 Si le runtime actuel est déjà lié à toutes les décisions de stratégie d’activation héritées de CLR version 2 (par exemple, en utilisant l' `useLegacyV2RuntimeActivationPolicy` attribut sur l' [ \<startup> élément](../../configure-apps/file-schema/startup/startup-element.md) dans le fichier de configuration), cette méthode ne retourne pas de résultat d’erreur ; à la place, le résultat est S_OK, comme c’est le cas si la méthode avait lié avec succès une stratégie d’activation héritée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRRuntimeInfo, interface](iclrruntimeinfo-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
- [\<startup> Appartient](../../configure-apps/file-schema/startup/startup-element.md)
