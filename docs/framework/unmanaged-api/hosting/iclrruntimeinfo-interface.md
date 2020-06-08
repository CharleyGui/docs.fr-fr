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
ms.openlocfilehash: 71e2c7f6790f29872c051bb5cea50755068057e9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504041"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo, interface
Fournit des méthodes qui retournent des informations sur un common language runtime spécifique (CLR), notamment la version, le répertoire et l’état de chargement. Cette interface fournit également des fonctionnalités spécifiques au runtime sans initialiser le Runtime. Il comprend la méthode [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) relative au runtime, la méthode [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) spécifique au module Runtime et les interfaces fournies par le runtime via la méthode [GetInterface](iclrruntimeinfo-getinterface-method.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime, méthode](iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Lie ce Runtime pour toutes les décisions de stratégie d’activation CLR version 2 héritées.|  
|[GetDefaultStartupFlags, méthode](iclrruntimeinfo-getdefaultstartupflags-method.md)|Obtient les indicateurs de démarrage CLR et le fichier de configuration hôte.|  
|[GetInterface, méthode](iclrruntimeinfo-getinterface-method.md)|Charge le CLR dans le processus en cours et retourne des pointeurs d’interface de Runtime, tels que [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md) et [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md). Cette méthode remplace toutes les `CorBindTo*` fonctions.|  
|[GetProcAddress, méthode](iclrruntimeinfo-getprocaddress-method.md)|Obtient l’adresse d’une fonction spécifiée qui a été exportée à partir du CLR associé à cette interface. Cette méthode remplace la méthode [GetRealProcAddress,](getrealprocaddress-function.md) .|  
|[GetRuntimeDirectory, méthode](iclrruntimeinfo-getruntimedirectory-method.md)|Obtient le répertoire d’installation du CLR associé à cette interface. Cette méthode remplace la méthode [GetCORSystemDirectory](getcorsystemdirectory-function.md) .|  
|[GetVersionString, méthode](iclrruntimeinfo-getversionstring-method.md)|Obtient les informations de version de common language runtime (CLR) associées à une interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) donnée. Cette méthode remplace les méthodes [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md) et [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) .|  
|[IsLoadable, méthode](iclrruntimeinfo-isloadable-method.md)|Indique si le runtime associé à cette interface peut être chargé dans le processus en cours, en tenant compte d’autres runtimes qui peuvent déjà être chargés dans le processus.|  
|[IsLoaded, méthode](iclrruntimeinfo-isloaded-method.md)|Indique si le CLR associé à l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) est chargé dans un processus.|  
|[IsStarted, méthode](iclrruntimeinfo-isstarted-method.md)|Indique si le CLR associé à l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) a été démarré.|  
|[LoadErrorString, méthode](iclrruntimeinfo-loaderrorstring-method.md)|Convertit une valeur HRESULT en un message d’erreur approprié pour la culture spécifiée. Cette méthode remplace les méthodes [LoadStringRC,](loadstringrc-function.md) et [LoadStringRCEx,](loadstringrcex-function.md) .|  
|[LoadLibrary, méthode](iclrruntimeinfo-loadlibrary-method.md)|Charge une bibliothèque à partir du répertoire Framework du CLR représenté par une interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) . Cette méthode remplace la méthode [LoadLibraryShim](loadlibraryshim-function.md) .|  
|[SetDefaultStartupFlags, méthode](iclrruntimeinfo-setdefaultstartupflags-method.md)|Définit les indicateurs de démarrage CLR et le fichier de configuration hôte.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hosting](index.md)
