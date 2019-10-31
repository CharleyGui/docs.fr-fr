---
title: ICorRuntimeHost, interface
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
ms.openlocfilehash: e66e1468a864ec85d88f759c481c7a9707d37f7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139550"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost, interface
Fournit des méthodes qui permettent à l’hôte de démarrer et d’arrêter explicitement le common language runtime (CLR) pour créer et configurer des domaines d’application, pour accéder au domaine par défaut et pour énumérer tous les domaines qui s’exécutent dans le processus.  
  
 Dans le .NET Framework version 2,0, cette interface est remplacée par [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CloseEnum, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|Réinitialise un énumérateur de domaine au début de la liste de domaines.|  
|[CreateDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|Crée un domaine d’application. L’appelant reçoit un pointeur d’interface de type <xref:System._AppDomain> à une instance de type <xref:System.AppDomain?displayProperty=nameWithType>.|  
|[CreateDomainEx, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|Crée un domaine d’application. Cette méthode permet à l’appelant de passer une instance IAppDomainSetup pour configurer des fonctionnalités supplémentaires de l’instance de <xref:System._AppDomain> retournée.|  
|[CreateDomainSetup, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|Obtient un pointeur d’interface de type `IAppDomainSetup` à une instance <xref:System.AppDomainSetup>. `IAppDomainSetup` fournit des méthodes pour configurer les aspects d’un domaine d’application avant qu’il ne soit créé.|  
|[CreateEvidence, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|Obtient un pointeur d’interface de type <xref:System.Security.Principal.IIdentity>, qui permet à l’hôte de créer une preuve de sécurité à passer à [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) ou [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).|  
|[CreateLogicalThreadState, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|Ne pas utiliser.|  
|[CurrentDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|Obtient un pointeur d’interface de type <xref:System._AppDomain> qui représente le domaine chargé sur le thread actuel.|  
|[DeleteLogicalThreadState, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|Ne pas utiliser.|  
|[EnumDomains, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|Obtient un énumérateur pour les domaines du processus en cours.|  
|[GetConfiguration, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|Obtient un objet qui permet à l’hôte de spécifier la configuration de rappel du CLR.|  
|[GetDefaultDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|Obtient un pointeur d’interface de type <xref:System._AppDomain> qui représente le domaine par défaut pour le processus actuel.|  
|[LocksHeldByLogicalThread, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|Ne pas utiliser.|  
|[MapFile, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|Mappe le fichier spécifié en mémoire. Cette méthode est obsolète.|  
|[NextDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|Obtient un pointeur d’interface vers le domaine suivant dans l’énumération.|  
|[Start, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|Démarre le CLR.|  
|[Stop, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|Arrête l’exécution du code dans le runtime pour le processus en cours.|  
|[SwitchInLogicalThreadState, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|Ne pas utiliser.|  
|[SwitchOutLogicalThreadState, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|Ne pas utiliser.|  
|[UnloadDomain, méthode](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|Décharge le domaine d’application spécifié du processus en cours.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :** 1,0, 1,1  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.AppDomain>
- [Hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRRuntimeHost, interface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [Hôtes du runtime](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost, coclasse](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
