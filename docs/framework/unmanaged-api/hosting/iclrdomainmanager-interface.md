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
ms.openlocfilehash: dda243ccbf18f396c1bcc03358997ea0f06c42a8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615707"
---
# <a name="iclrdomainmanager-interface"></a>ICLRDomainManager, interface
Permet à l’hôte de spécifier le gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut et pour spécifier les propriétés d’initialisation.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[SetAppDomainManagerType, méthode](iclrdomainmanager-setappdomainmanagertype-method.md)|Spécifie le type, dérivé de la <xref:System.AppDomainManager?displayProperty=nameWithType> classe, du gestionnaire de domaine d’application qui sera utilisé pour initialiser le domaine d’application par défaut.|  
|[SetPropertiesForDefaultAppDomain, méthode](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|Définit les propriétés qui seront utilisées pour initialiser le domaine d’application par défaut.|  
  
## <a name="remarks"></a>Notes  
 Pour récupérer une instance de cette interface, appelez la méthode [ICLRControl :: GetCLRManager](iclrcontrol-getclrmanager-method.md) avec l’IID de type Manager `IID_ICLRDomainManager` .  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d'hébergement](hosting-interfaces.md)
- [Hébergement](index.md)
