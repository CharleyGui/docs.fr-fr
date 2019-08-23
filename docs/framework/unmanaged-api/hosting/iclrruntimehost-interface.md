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
ms.openlocfilehash: 0f159c0b57f2087b608fac8cbc9b9c64ceb063a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965989"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost, interface
Fournit des fonctionnalités similaires à celles de l’interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) fournie dans la .NET Framework version 1, avec les modifications suivantes:  
  
- Ajout de la méthode [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) pour définir l’interface de contrôle hôte.  
  
- Omission de certaines méthodes fournies par `ICorRuntimeHost`.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ExecuteApplication, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|Utilisé dans les scénarios de déploiement ClickOnce basés sur un manifeste pour spécifier l’application à activer dans un nouveau domaine.|  
|[ExecuteInAppDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|Spécifie <xref:System.AppDomain> le dans lequel exécuter le code managé spécifié.|  
|[ExecuteInDefaultAppDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|Appelle la méthode spécifiée du type spécifié dans l’assembly spécifié.|  
|[GetCLRControl, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Obtient un pointeur d’interface de type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) que les hôtes peuvent utiliser pour personnaliser les aspects du Common Language Runtime (CLR).|  
|[GetCurrentAppDomainId, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|Obtient l’identificateur numérique du en cours <xref:System.AppDomain> d’exécution.|  
|[SetHostControl, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|Définit l’interface de contrôle hôte. Vous devez appeler `SetHostControl` avant d' `Start`appeler.|  
|[Start, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|Initialise le CLR dans un processus.|  
|[Stop, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|Arrête l’exécution du code par le Runtime.|  
|[UnloadAppDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|Décharge le <xref:System.AppDomain> qui correspond à l’identificateur numérique spécifié.|  
  
## <a name="remarks"></a>Notes  
 À partir du .NET Framework 4, utilisez l’interface [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) pour obtenir un pointeur vers l’interface [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , puis appelez la méthode [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) pour obtenir un pointeur vers `ICLRRuntimeHost`. Dans les versions antérieures du .NET Framework, l’hôte obtient un pointeur vers une `ICLRRuntimeHost` instance en appelant [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime,](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md). Pour fournir des implémentations de l’une des technologies fournies dans le .NET Framework version 2,0, vous devez `ICLRRuntimeHost` utiliser au `ICorRuntimeHost`lieu de.  
  
> [!IMPORTANT]
> N’appelez pas la méthode [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) avant d’appeler la méthode [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) pour activer une application basée sur un manifeste. Si la `Start` méthode est appelée en premier, `ExecuteApplication` l’appel de la méthode échoue.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CorBindToCurrentRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICLRControl, interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICorRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CLRRuntimeHost, coclasse](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
