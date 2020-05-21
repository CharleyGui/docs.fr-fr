---
title: ICLRRuntimeInfo::IsLoaded, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: 3275a69683a312340f35841815685066def10b23
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762524"
---
# <a name="iclrruntimeinfoisloaded-method"></a>ICLRRuntimeInfo::IsLoaded, méthode
Indique si le common language runtime (CLR) associé à l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) est chargé dans un processus. Un Runtime peut être chargé sans également être démarré.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a>Paramètres  
 `hndProcess`  
 dans Handle du processus.  
  
 `pbLoaded`  
 [out] `true` Si le CLR est chargé dans le processus ; Sinon, `false` .  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pbLoaded` a la valeur null.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est à compatibilité descendante avec les fonctions et interfaces suivantes :  
  
- [ICorRuntimeHost](icorruntimehost-interface.md) , interface (dans l’API d’hébergement .NET Framework version 1).  
  
- [ICLRRuntimeHost](iclrruntimehost-interface.md) , interface (dans l’API d’hébergement .NET Framework 2,0).  
  
- Fonctions déconseillées `CorBindTo*` (consultez [fonctions d’hébergement CLR dépréciées](deprecated-clr-hosting-functions.md) dans l’API d’hébergement .NET Framework 2,0).  
  
 Un hôte peut appeler l’une des fonctions dépréciées `CorBindTo*` , telles que la fonction [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) , pour instancier une version spécifique du CLR. L’hôte peut ensuite appeler la méthode [ICLRMetaHost :: GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) et spécifier le même numéro de version pour obtenir une interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .  
  
 Si l’hôte appelle ensuite la `IsLoaded` méthode sur l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) retournée, `pbLoaded` retourne `true` ; sinon, il retourne `false` .  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRRuntimeInfo, interface](iclrruntimeinfo-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
