---
title: ICLRMetaHost::RequestRuntimeLoadedNotification, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 539f69c33b67ad1a8a514062c5d777deaced1599
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965007"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification, méthode
Fournit une fonction de rappel dont l’appel est garanti quand une version de common language runtime (CLR) est chargée pour la première fois, mais qu’elle n’a pas encore démarré. Cette méthode remplace la fonction [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pCallbackFunction`  
 dans Fonction de rappel qui est appelée lorsqu’un nouveau Runtime a été chargé.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`pCallbackFunction` a la valeur null.|  
  
## <a name="remarks"></a>Notes  
 Le rappel fonctionne de la façon suivante:  
  
- Le rappel est appelé uniquement lorsqu’un Runtime est chargé pour la première fois.  
  
- Le rappel n’est pas appelé pour les charges réentrantes du même Runtime.  
  
- Pour les chargements de Runtime non réentrants, les appels à la fonction de rappel sont sérialisés.  
  
 La fonction de rappel a le prototype suivant:  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 Les prototypes de fonction de rappel sont les suivants:  
  
- `pfnCallbackThreadSet`:  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- `pfnCallbackThreadUnset`:  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 Si l’hôte envisage de charger ou de faire en sorte qu’un autre Runtime soit chargé de manière réentrante, les `pfnCallbackThreadSet` paramètres et `pfnCallbackThreadUnset` fournis dans la fonction de rappel doivent être utilisés de la façon suivante:  
  
- `pfnCallbackThreadSet`doit être appelé par le thread qui peut provoquer un chargement du runtime avant une tentative de chargement.  
  
- `pfnCallbackThreadUnset`doit être appelé lorsque le thread n’entraîne plus de charge d’exécution de ce type (et avant de retourner le rappel initial).  
  
- `pfnCallbackThreadSet`et `pfnCallbackThreadUnset` sont tous deux non réentrants.  
  
> [!NOTE]
> Les `pfnCallbackThreadUnset` `pfnCallbackThreadSet` applicationshôtesnedoiventpasappeleretendehorsdelaportéeduparamètre.`pCallbackFunction`  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRMetaHost, interface](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
