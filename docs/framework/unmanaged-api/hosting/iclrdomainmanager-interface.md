---
title: ICLRDomainManager, interface
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
ms.openlocfilehash: a5abb601fe795a0c615403eec69f68ad9f66f00f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681169"
---
# <a name="iclrdomainmanager-interface"></a>ICLRDomainManager, interface

Permet à l’hôte de spécifier le gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut et pour spécifier les propriétés d’initialisation.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[SetAppDomainManagerType, méthode](iclrdomainmanager-setappdomainmanagertype-method.md)|Spécifie le type, dérivé de la <xref:System.AppDomainManager?displayProperty=nameWithType> classe, du gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut.|  
|[SetPropertiesForDefaultAppDomain, méthode](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|Définit les propriétés qui seront utilisées pour initialiser le domaine d’application par défaut.|  
  
## <a name="remarks"></a>Remarques  

 Pour récupérer une instance de cette interface, appelez la méthode [ICLRControl :: GetCLRManager](iclrcontrol-getclrmanager-method.md) avec l’IID de type Manager `IID_ICLRDomainManager` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
