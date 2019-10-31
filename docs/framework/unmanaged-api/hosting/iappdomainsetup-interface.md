---
title: IAppDomainSetup, interface
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
ms.openlocfilehash: 0fab64c31d4a73995c16d21767f4569f21c7df9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126869"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup, interface
Fournit des propriétés qui permettent à l’hôte de configurer un type de <xref:System.AppDomain?displayProperty=nameWithType> avant d’appeler la méthode [ICorRuntimeHost :: CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) pour le créer.  
  
## <a name="properties"></a>Propriétés  
  
|Property|Description|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Obtient ou définit le nom du répertoire qui contient l’application.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Obtient ou définit le nom de l'application.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Obtient ou définit le nom d’une zone spécifique à l’application dans laquelle les fichiers sont des clichés instantanés.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Obtient ou définit le nom du fichier de configuration pour une application.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Obtient ou définit le nom du répertoire dans lequel les fichiers générés dynamiquement sont stockés et accessibles.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Obtient ou définit le chemin d’accès au fichier de licence associé à ce domaine.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Obtient ou définit la liste des répertoires combinés avec le répertoire <xref:System.AppDomainSetup.ApplicationBase%2A> pour détecter les assemblys privés.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Obtient ou définit une valeur de chaîne qui inclut ou exclut <xref:System.AppDomainSetup.ApplicationBase%2A> du chemin de recherche de l’application.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Obtient ou définit les noms des répertoires qui contiennent des assemblys pour lesquels des clichés instantanés doivent être définis.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Obtient ou définit une chaîne qui indique si la copie fictive est activée ou désactivée. Les valeurs valides sont « true » ou « false ».|  
  
## <a name="remarks"></a>Notes  
 L’interface `IAppDomainSetup` correspond à l’interface <xref:System.IAppDomainSetup> managée, que le type de <xref:System.AppDomainSetup> implémente. Pour obtenir une description détaillée de ses propriétés, consultez <xref:System.IAppDomainSetup?displayProperty=nameWithType>.  
  
 `IAppDomainSetup` représente des informations de liaison d’assembly qui peuvent être ajoutées à une instance de <xref:System.AppDomain> avant sa création. Par exemple, un hôte peut définir la propriété <xref:System.AppDomainSetup.ApplicationBase%2A> pour établir un répertoire racine, que le common language runtime (CLR) sonde pour les assemblys managés.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [Interfaces d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
