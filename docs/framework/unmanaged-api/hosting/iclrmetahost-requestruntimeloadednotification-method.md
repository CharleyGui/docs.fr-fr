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
ms.openlocfilehash: 6813f72f9d27aeff90f797a6ca9370b22e03e6f0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703694"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a>ICLRMetaHost::RequestRuntimeLoadedNotification, méthode
Fournit une fonction de rappel dont l’appel est garanti quand une version de common language runtime (CLR) est chargée pour la première fois, mais qu’elle n’a pas encore démarré. Cette méthode remplace la fonction [LockClrVersion](lockclrversion-function.md) .  
  
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
 Le rappel fonctionne de la façon suivante :  
  
- Le rappel est appelé uniquement lorsqu’un Runtime est chargé pour la première fois.  
  
- Le rappel n’est pas appelé pour les charges réentrantes du même Runtime.  
  
- Pour les chargements de Runtime non réentrants, les appels à la fonction de rappel sont sérialisés.  
  
 La fonction de rappel a le prototype suivant :  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 Les prototypes de fonction de rappel sont les suivants :  
  
- `pfnCallbackThreadSet`:  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- `pfnCallbackThreadUnset`:  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 Si l’hôte envisage de charger ou de faire en sorte qu’un autre Runtime soit chargé de manière réentrante, les `pfnCallbackThreadSet` `pfnCallbackThreadUnset` paramètres et fournis dans la fonction de rappel doivent être utilisés de la façon suivante :  
  
- `pfnCallbackThreadSet`doit être appelé par le thread qui peut provoquer un chargement du runtime avant une tentative de chargement.  
  
- `pfnCallbackThreadUnset`doit être appelé lorsque le thread n’entraîne plus de charge d’exécution de ce type (et avant de retourner le rappel initial).  
  
- `pfnCallbackThreadSet`et `pfnCallbackThreadUnset` sont tous deux non réentrants.  
  
> [!NOTE]
> Les applications hôtes ne doivent pas appeler `pfnCallbackThreadSet` et `pfnCallbackThreadUnset` en dehors de la portée du `pCallbackFunction` paramètre.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRMetaHost, interface](iclrmetahost-interface.md)
- [Hébergement](index.md)
