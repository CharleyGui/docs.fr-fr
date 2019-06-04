---
title: ICLRRuntimeHost, interface
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba02373aae33baf77b72323fabf1f6ca1fe4eecf
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490240"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost, interface
Fournit des fonctionnalités similaires à celles de la [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface fournie dans le .NET Framework version 1, avec les modifications suivantes :  
  
- L’ajout de la [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) méthode pour définir l’interface de contrôle hôte.  
  
- L’omission de certaines méthodes fournies par `ICorRuntimeHost`.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ExecuteApplication, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|Utilisé dans les scénarios de déploiement ClickOnce basée sur un manifeste pour spécifier l’application à activer dans un nouveau domaine.|  
|[ExecuteInAppDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|Spécifie le <xref:System.AppDomain> dans lequel exécuter le code managé spécifié.|  
|[ExecuteInDefaultAppDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|Appelle la méthode spécifiée du type spécifié dans l’assembly spécifié.|  
|[GetCLRControl, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Obtient un pointeur d’interface de type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) que les hôtes peuvent utiliser pour personnaliser les aspects du common language runtime (CLR).|  
|[GetCurrentAppDomainId, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|Obtient l’identificateur numérique de la <xref:System.AppDomain> qui est en cours d’exécution.|  
|[SetHostControl, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|Définit l’interface de contrôle hôte. Vous devez appeler `SetHostControl` avant d’appeler `Start`.|  
|[Start, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|Initialise le CLR dans un processus.|  
|[Stop, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|Arrête l’exécution du code par le runtime.|  
|[UnloadAppDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|Décharge le <xref:System.AppDomain> qui correspond à l’identificateur numérique spécifié.|  
  
## <a name="remarks"></a>Notes  
 À compter de .NET Framework 4, utilisez le [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface permettant d’obtenir un pointeur vers le [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, puis appelez le [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)méthode pour obtenir un pointeur vers `ICLRRuntimeHost`. Dans les versions antérieures du .NET Framework, l’hôte obtient un pointeur vers un `ICLRRuntimeHost` instance en appelant [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md). Pour fournir des implémentations de chacune des technologies fournies dans le .NET Framework version 2.0, vous devez utiliser `ICLRRuntimeHost` au lieu de `ICorRuntimeHost`.  
  
> [!IMPORTANT]
>  N’appelez pas la [Démarrer](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) méthode avant d’appeler le [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) méthode permettant d’activer une application basée sur un manifeste. Si le `Start` méthode est appelée en premier, le `ExecuteApplication` appel de méthode échoue.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CorBindToCurrentRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICLRControl, interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICorRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CLRRuntimeHost, coclasse](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
