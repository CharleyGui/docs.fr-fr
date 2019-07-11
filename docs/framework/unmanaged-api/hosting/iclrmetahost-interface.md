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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45089d1b64264e000c07603808f0c5fb1263b042
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776571"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost, interface
Fournit des méthodes qui retournent une version spécifique du common language runtime (CLR) en fonction de son numéro de version, répertorient tous les installés, listent de tous les runtimes chargés dans un processus spécifié, découvrir la version CLR utilisée pour compiler un assembly, de quitter un processus avec un arrêt de runtime normal et une liaison héritée de l’API de requête.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|Retourne une énumération qui contient un élément valide [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) pointeur d’interface pour chaque version du CLR qui est installée sur un ordinateur.|  
|[EnumerateLoadedRuntimes, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|Retourne une énumération qui contient un élément valide [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) pointeur d’interface pour chaque CLR qui est chargé dans un processus donné. Cette méthode remplace [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md).|  
|[ExitProcess, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|Tente d’arrêter correctement les runtimes tous chargés et puis met fin au processus. Remplace le [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) (fonction).|  
|[GetRuntime, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|Obtient le [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface qui correspond à une version particulière du CLR. Cette méthode remplace la [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) fonction utilisée avec le [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) indicateur.|  
|[GetVersionFromFile, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|Obtient d’origine compilation version du .NET Framework l’assembly (stockée dans les métadonnées), son chemin d’accès donnée. Cette méthode remplace [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md).|  
|[QueryLegacyV2RuntimeBinding, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|Retourne une interface qui représente un runtime auquel stratégie d’activation héritée a été liée, par exemple à l’aide de la `useLegacyV2RuntimeActivationPolicy` d’attribut sur le [ \<démarrage > élément](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) entrée de fichier de configuration, en utilisant directement des API d’activation hérité ou en appelant le [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) (méthode).|  
|[RequestRuntimeLoadedNotification, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|Garantit un rappel pour le pointeur de fonction spécifié lorsqu’une version du CLR est chargée en premier, mais pas encore démarrée. Cette méthode remplace [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)|  
  
## <a name="remarks"></a>Notes  
 La seule façon d’obtenir une instance de cette interface est en appelant le [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) fonctionnent comme suit :  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MetaHost.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
