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
ms.openlocfilehash: d504101747995557ba526c88de451ebab7b3c556
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698555"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup, interface

Fournit des propriétés qui permettent à l’hôte de configurer un <xref:System.AppDomain?displayProperty=nameWithType> type avant d’appeler la méthode [ICorRuntimeHost :: CreateDomainEx](icorruntimehost-createdomainex-method.md) pour le créer.  
  
## <a name="properties"></a>Propriétés  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Obtient ou définit le nom du répertoire qui contient l’application.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Obtient ou définit le nom de l'application.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Obtient ou définit le nom d’une zone spécifique à l’application dans laquelle les fichiers sont des clichés instantanés.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Obtient ou définit le nom du fichier de configuration pour une application.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Obtient ou définit le nom du répertoire dans lequel les fichiers générés dynamiquement sont stockés et accessibles.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Obtient ou définit le chemin d’accès au fichier de licence associé à ce domaine.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Obtient ou définit la liste des répertoires combinés avec le <xref:System.AppDomainSetup.ApplicationBase%2A> répertoire pour détecter les assemblys privés.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Obtient ou définit une valeur de chaîne qui inclut ou exclut du <xref:System.AppDomainSetup.ApplicationBase%2A> chemin de recherche de l’application.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Obtient ou définit les noms des répertoires qui contiennent des assemblys pour lesquels des clichés instantanés doivent être définis.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Obtient ou définit une chaîne qui indique si la copie fictive est activée ou désactivée. Les valeurs valides sont « true » ou « false ».|  
  
## <a name="remarks"></a>Remarques  

 L' `IAppDomainSetup` interface correspond à l’interface managée <xref:System.IAppDomainSetup> , que le <xref:System.AppDomainSetup> type implémente. Pour obtenir une <xref:System.IAppDomainSetup?displayProperty=nameWithType> Description détaillée de ses propriétés, consultez.  
  
 `IAppDomainSetup` représente les informations de liaison d’assembly qui peuvent être ajoutées à une <xref:System.AppDomain> instance avant sa création. Par exemple, un hôte peut définir la <xref:System.AppDomainSetup.ApplicationBase%2A> propriété pour établir un répertoire racine, que le Common Language Runtime (CLR) sonde pour les assemblys managés.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [Interfaces d'hébergement](hosting-interfaces.md)
