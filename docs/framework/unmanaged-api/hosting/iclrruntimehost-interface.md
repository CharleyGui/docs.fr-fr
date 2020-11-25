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
ms.openlocfilehash: 8d88222215eb31e1c63f3b26079517c4b088e81b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728834"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost, interface

Fournit des fonctionnalités similaires à celles de l’interface [ICorRuntimeHost](icorruntimehost-interface.md) fournie dans la .NET Framework version 1, avec les modifications suivantes :  
  
- Ajout de la méthode [SetHostControl](iclrruntimehost-sethostcontrol-method.md) pour définir l’interface de contrôle hôte.  
  
- Omission de certaines méthodes fournies par `ICorRuntimeHost` .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ExecuteApplication, méthode](iclrruntimehost-executeapplication-method.md)|Utilisé dans les scénarios de déploiement ClickOnce basés sur un manifeste pour spécifier l’application à activer dans un nouveau domaine.|  
|[ExecuteInAppDomain, méthode](iclrruntimehost-executeinappdomain-method.md)|Spécifie le <xref:System.AppDomain> dans lequel exécuter le code managé spécifié.|  
|[ExecuteInDefaultAppDomain, méthode](iclrruntimehost-executeindefaultappdomain-method.md)|Appelle la méthode spécifiée du type spécifié dans l’assembly spécifié.|  
|[GetCLRControl, méthode](iclrruntimehost-getclrcontrol-method.md)|Obtient un pointeur d’interface de type [ICLRControl](iclrcontrol-interface.md) que les hôtes peuvent utiliser pour personnaliser les aspects du Common Language Runtime (CLR).|  
|[GetCurrentAppDomainId, méthode](iclrruntimehost-getcurrentappdomainid-method.md)|Obtient l’identificateur numérique du en <xref:System.AppDomain> cours d’exécution.|  
|[SetHostControl, méthode](iclrruntimehost-sethostcontrol-method.md)|Définit l’interface de contrôle hôte. Vous devez appeler `SetHostControl` avant d’appeler `Start` .|  
|[Start, méthode](iclrruntimehost-start-method.md)|Initialise le CLR dans un processus.|  
|[Stop (méthode)](iclrruntimehost-stop-method.md)|Arrête l’exécution du code par le Runtime.|  
|[UnloadAppDomain, méthode](iclrruntimehost-unloadappdomain-method.md)|Décharge le <xref:System.AppDomain> qui correspond à l’identificateur numérique spécifié.|  
  
## <a name="remarks"></a>Remarques  

 À partir du .NET Framework 4, utilisez l’interface [ICLRMetaHost](iclrmetahost-interface.md) pour obtenir un pointeur vers l’interface [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , puis appelez la méthode [ICLRRuntimeInfo :: GetInterface](iclrruntimeinfo-getinterface-method.md) pour obtenir un pointeur vers `ICLRRuntimeHost` . Dans les versions antérieures du .NET Framework, l’hôte obtient un pointeur vers une `ICLRRuntimeHost` instance en appelant [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime,](corbindtocurrentruntime-function.md). Pour fournir des implémentations de l’une des technologies fournies dans le .NET Framework version 2,0, vous devez utiliser `ICLRRuntimeHost` au lieu de `ICorRuntimeHost` .  
  
> [!IMPORTANT]
> N’appelez pas la méthode [Start](iclrruntimehost-start-method.md) avant d’appeler la méthode [ExecuteApplication](iclrruntimehost-executeapplication-method.md) pour activer une application basée sur un manifeste. Si la `Start` méthode est appelée en premier, l’appel de la `ExecuteApplication` méthode échoue.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CorBindToCurrentRuntime, fonction](corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx, fonction](corbindtoruntimeex-function.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
- [ICorRuntimeHost, interface](icorruntimehost-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Coclasse CLRRuntimeHost](clrruntimehost-coclass.md)
