---
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
ms.openlocfilehash: b9a51a85bd17e527d4c04b69ca65100a7069607f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703715"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a>ICLRMetaHost::QueryLegacyV2RuntimeBinding, méthode
Retourne une interface qui représente un runtime auquel une stratégie d’activation héritée a été liée, par exemple, en utilisant l' `useLegacyV2RuntimeActivationPolicy` attribut sur l’entrée du fichier de configuration de l' [ \< élément de démarrage>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , en utilisant directement les API d’activation héritées ou en appelant la méthode [ICLRRuntimeInfo :: BindAsLegacyV2Runtime,](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>Paramètres  
 `riid`  
 dans Obligatoire. actuellement, la seule valeur valide pour ce paramètre est `IID_ICLRRuntimeInfo` .  
  
 `ppUnk`  
 [out] Obligatoire. Lorsque cette méthode est retournée, contient un pointeur vers l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) qui représente un Runtime lié à une stratégie d’activation héritée.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La méthode s'est terminée correctement et a retourné un runtime lié à une stratégie d'activation héritée.|  
|S_FALSE|La méthode s'est terminée correctement, mais un runtime hérité n'a pas encore été lié.|  
|E_NOINTERFACE|La méthode a trouvé un runtime lié à une stratégie d'activation héritée, mais `riid` n'est pas pris en charge par ce runtime.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRMetaHost, interface](iclrmetahost-interface.md)
- [Hébergement](index.md)
