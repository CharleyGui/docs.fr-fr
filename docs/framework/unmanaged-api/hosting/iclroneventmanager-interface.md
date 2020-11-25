---
title: ICLROnEventManager, interface
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
ms.openlocfilehash: 1948075d87b5a44397a1eaab3adb4edbc96d7143
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725629"
---
# <a name="iclroneventmanager-interface"></a>ICLROnEventManager, interface

Fournit des méthodes qui permettent à l’hôte d’inscrire et d’annuler l’enregistrement des rappels pour les événements common language runtime (CLR).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[RegisterActionOnEvent, méthode](iclroneventmanager-registeractiononevent-method.md)|Inscrit un pointeur de rappel pour l’événement spécifié.|  
|[UnregisterActionOnEvent, méthode](iclroneventmanager-unregisteractiononevent-method.md)|Annule l’inscription d’un pointeur de rappel précédemment inscrit pour l’événement spécifié.|  
  
## <a name="remarks"></a>Remarques  

 Pour inscrire et désinscrire des rappels d’événements, l’hôte obtient une référence à `ICLROnEventManager` en appelant la méthode [ICLRControl :: GetCLRManager](iclrcontrol-getclrmanager-method.md) .  
  
> [!NOTE]
> Les événements décrits par [EClrEvent](eclrevent-enumeration.md) peuvent être déclenchés plusieurs fois et à partir de différents threads pour signaler un déchargement ou la désactivation du CLR.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EClrEvent, énumération](eclrevent-enumeration.md)
- [IActionOnCLREvent, interface](iactiononclrevent-interface.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
