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
ms.openlocfilehash: 9fcb5e189af9f72de7635aad550a5e8ab5522dbd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720618"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost, interface

Fournit des méthodes qui permettent à l’hôte de démarrer et d’arrêter explicitement le common language runtime (CLR) pour créer et configurer des domaines d’application, pour accéder au domaine par défaut et pour énumérer tous les domaines qui s’exécutent dans le processus.  
  
 Dans le .NET Framework version 2,0, cette interface est remplacée par [ICLRRuntimeHost](iclrruntimehost-interface.md).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CloseEnum, méthode](icorruntimehost-closeenum-method.md)|Réinitialise un énumérateur de domaine au début de la liste de domaines.|  
|[CreateDomain, méthode](icorruntimehost-createdomain-method.md)|Crée un domaine d’application. L’appelant reçoit un pointeur d’interface de type <xref:System._AppDomain> vers une instance de type <xref:System.AppDomain?displayProperty=nameWithType> .|  
|[CreateDomainEx, méthode](icorruntimehost-createdomainex-method.md)|Crée un domaine d’application. Cette méthode permet à l’appelant de passer une instance IAppDomainSetup pour configurer des fonctionnalités supplémentaires de l’instance retournée <xref:System._AppDomain> .|  
|[CreateDomainSetup, méthode](icorruntimehost-createdomainsetup-method.md)|Obtient un pointeur d’interface de type `IAppDomainSetup` vers une <xref:System.AppDomainSetup> instance. `IAppDomainSetup` fournit des méthodes pour configurer les aspects d’un domaine d’application avant qu’il ne soit créé.|  
|[CreateEvidence, méthode](icorruntimehost-createevidence-method.md)|Obtient un pointeur d’interface de type <xref:System.Security.Principal.IIdentity> , qui permet à l’hôte de créer une preuve de sécurité à passer à [CreateDomain](icorruntimehost-createdomain-method.md) ou [CreateDomainEx](icorruntimehost-createdomainex-method.md).|  
|[CreateLogicalThreadState, méthode](icorruntimehost-createlogicalthreadstate-method.md)|Ne pas utiliser.|  
|[CurrentDomain, méthode](icorruntimehost-currentdomain-method.md)|Obtient un pointeur d’interface de type <xref:System._AppDomain> qui représente le domaine chargé sur le thread actuel.|  
|[DeleteLogicalThreadState, méthode](icorruntimehost-deletelogicalthreadstate-method.md)|Ne pas utiliser.|  
|[EnumDomains, méthode](icorruntimehost-enumdomains-method.md)|Obtient un énumérateur pour les domaines du processus en cours.|  
|[GetConfiguration, méthode](icorruntimehost-getconfiguration-method.md)|Obtient un objet qui permet à l’hôte de spécifier la configuration de rappel du CLR.|  
|[GetDefaultDomain, méthode](icorruntimehost-getdefaultdomain-method.md)|Obtient un pointeur d’interface de type <xref:System._AppDomain> qui représente le domaine par défaut pour le processus en cours.|  
|[LocksHeldByLogicalThread, méthode](icorruntimehost-locksheldbylogicalthread-method.md)|Ne pas utiliser.|  
|[MapFile, méthode](icorruntimehost-mapfile-method.md)|Mappe le fichier spécifié en mémoire. Cette méthode est obsolète.|  
|[NextDomain, méthode](icorruntimehost-nextdomain-method.md)|Obtient un pointeur d’interface vers le domaine suivant dans l’énumération.|  
|[Start, méthode](icorruntimehost-start-method.md)|Démarre le CLR.|  
|[Stop (méthode)](icorruntimehost-stop-method.md)|Arrête l’exécution du code dans le runtime pour le processus en cours.|  
|[SwitchInLogicalThreadState, méthode](icorruntimehost-switchinlogicalthreadstate-method.md)|Ne pas utiliser.|  
|[SwitchOutLogicalThreadState, méthode](icorruntimehost-switchoutlogicalthreadstate-method.md)|Ne pas utiliser.|  
|[UnloadDomain, méthode](icorruntimehost-unloaddomain-method.md)|Décharge le domaine d’application spécifié du processus en cours.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :** 1,0, 1,1  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.AppDomain>
- [Hébergement](index.md)
- [ICLRRuntimeHost, interface](iclrruntimehost-interface.md)
- [Hôtes du runtime](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [Interfaces d'hébergement](hosting-interfaces.md)
- [CorRuntimeHost, coclasse](corruntimehost-coclass.md)
