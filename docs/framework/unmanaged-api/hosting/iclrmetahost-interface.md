---
title: ICLRMetaHost, interface
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
ms.openlocfilehash: 391adc6f9fe55ad7ca527ea416956ab013a27b15
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703721"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost, interface
Fournit des méthodes qui retournent une version spécifique du common language runtime (CLR) en fonction de son numéro de version, de la liste de tous les CLR installés, de la liste de tous les runtimes chargés dans un processus spécifié, de la découverte de la version CLR utilisée pour compiler un assembly, de la sortie d’un processus avec arrêt du runtime propre et de la liaison d’API héritée  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|Retourne une énumération qui contient un pointeur d’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) valide pour chaque version du CLR installée sur un ordinateur.|  
|[EnumerateLoadedRuntimes, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|Retourne une énumération qui contient un pointeur d’interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) valide pour chaque CLR qui est chargé dans un processus donné. Cette méthode remplace [GetVersionFromProcess](getversionfromprocess-function.md).|  
|[ExitProcess, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|Tente d’arrêter correctement tous les runtimes chargés, puis termine le processus. Remplace la fonction [CorExitProcess,](corexitprocess-function.md) .|  
|[GetRuntime, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|Obtient l’interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) qui correspond à une version particulière du CLR. Cette méthode remplace la fonction [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) utilisée avec l’indicateur [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .|  
|[GetVersionFromFile, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|Obtient la version de compilation .NET Framework d’origine de l’assembly (stockée dans les métadonnées), en fonction de son chemin d’accès au fichier. Cette méthode remplace [GetFileVersion,](getfileversion-function.md).|  
|[QueryLegacyV2RuntimeBinding, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|Retourne une interface qui représente un runtime auquel une stratégie d’activation héritée a été liée, par exemple en utilisant l' `useLegacyV2RuntimeActivationPolicy` attribut sur l’entrée du fichier de configuration de l' [ \< élément de démarrage>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , en utilisant directement les API d’activation héritées ou en appelant la méthode [ICLRRuntimeInfo :: BindAsLegacyV2Runtime,](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .|  
|[RequestRuntimeLoadedNotification, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|Garantit un rappel au pointeur de fonction spécifié quand une version CLR est chargée pour la première fois, mais pas encore démarrée. Cette méthode remplace [LockClrVersion](lockclrversion-function.md)|  
  
## <a name="remarks"></a>Notes  
 La seule façon d’accéder à une instance de cette interface est d’appeler la fonction [CLRCreateInstance](clrcreateinstance-function.md) comme suit :  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
