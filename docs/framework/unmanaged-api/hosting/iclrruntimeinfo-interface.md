---
title: ICLRRuntimeInfo, interface
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo
helpviewer_keywords:
- ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 287e5ede-b3a7-4ef8-a756-4fca3f285a82
topic_type:
- apiref
ms.openlocfilehash: f6608b03df80fa37ebf5049b53bce46da3e155e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120361"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo, interface
Fournit des méthodes qui retournent des informations sur un common language runtime spécifique (CLR), notamment la version, le répertoire et l’état de chargement. Cette interface fournit également des fonctionnalités spécifiques au runtime sans initialiser le Runtime. Il comprend la méthode [LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) relative au runtime, la méthode [GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) spécifique au module Runtime et les interfaces fournies par le runtime via la méthode [GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Lie ce Runtime pour toutes les décisions de stratégie d’activation CLR version 2 héritées.|  
|[GetDefaultStartupFlags, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|Obtient les indicateurs de démarrage CLR et le fichier de configuration hôte.|  
|[GetInterface, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|Charge le CLR dans le processus en cours et retourne des pointeurs d’interface de Runtime, tels que [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) et [IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md). Cette méthode remplace toutes les fonctions `CorBindTo*`.|  
|[GetProcAddress, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|Obtient l’adresse d’une fonction spécifiée qui a été exportée à partir du CLR associé à cette interface. Cette méthode remplace la méthode [GetRealProcAddress,](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) .|  
|[GetRuntimeDirectory, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|Obtient le répertoire d’installation du CLR associé à cette interface. Cette méthode remplace la méthode [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) .|  
|[GetVersionString, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|Obtient les informations de version de common language runtime (CLR) associées à une interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) donnée. Cette méthode remplace les méthodes [GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) et [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) .|  
|[IsLoadable, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|Indique si le runtime associé à cette interface peut être chargé dans le processus en cours, en tenant compte d’autres runtimes qui peuvent déjà être chargés dans le processus.|  
|[IsLoaded, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|Indique si le CLR associé à l’interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) est chargé dans un processus.|  
|[IsStarted, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|Indique si le CLR associé à l’interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) a été démarré.|  
|[LoadErrorString, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|Convertit une valeur HRESULT en un message d’erreur approprié pour la culture spécifiée. Cette méthode remplace les méthodes [LoadStringRC,](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md) et [LoadStringRCEx,](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md) .|  
|[LoadLibrary, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|Charge une bibliothèque à partir du répertoire Framework du CLR représenté par une interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) . Cette méthode remplace la méthode [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) .|  
|[SetDefaultStartupFlags, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|Définit les indicateurs de démarrage CLR et le fichier de configuration hôte.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
