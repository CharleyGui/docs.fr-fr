---
title: IHostControl, interface
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 1bffef31702aa051d9ca865b18a67ac90c00cd00
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680654"
---
# <a name="ihostcontrol-interface"></a>IHostControl, interface

Fournit des méthodes pour la configuration du chargement des assemblys et pour déterminer les interfaces d’hébergement que l’hôte prend en charge.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetHostManager, méthode](ihostcontrol-gethostmanager-method.md)|Obtient un pointeur d’interface vers l’implémentation de l’hôte de l’interface avec le spécifié `IID` .|  
|[SetAppDomainManager, méthode](ihostcontrol-setappdomainmanager-method.md)|Avertit l’hôte qu’un domaine d’application a été créé.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.AppDomainManager>
- [ICLRRuntimeHost, interface](iclrruntimehost-interface.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
