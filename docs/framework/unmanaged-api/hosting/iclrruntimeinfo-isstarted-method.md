---
title: ICLRRuntimeInfo::IsStarted, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
ms.openlocfilehash: 1dfeb6101a6b8e33ab2fe35f318087d7f1834b6a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714885"
---
# <a name="iclrruntimeinfoisstarted-method"></a>ICLRRuntimeInfo::IsStarted, méthode

Indique si le runtime a été démarré (c’est-à-dire, si la [méthode ICLRRuntimeHost :: Start](iclrruntimehost-start-method.md) a été appelée et a réussi).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pbStarted`  
 [out] `true` Si ce Runtime est démarré ; Sinon, `false` .  
  
 `pdwStartupFlags`  
 à Retourne les indicateurs utilisés pour démarrer le Runtime.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_NOTIMPL|La version du common language runtime (CLR) est antérieure à la version CLR du .NET Framework 4.|  
  
## <a name="remarks"></a>Remarques  

 Cette méthode ne fonctionne pas avec les versions CLR antérieures à la version CLR du .NET Framework 4.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRRuntimeInfo, interface](iclrruntimeinfo-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
