---
title: IActionOnCLREvent, interface
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: 4e72cd8bee2cb4f35155d7b99cfe8d9cf63f463a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616071"
---
# <a name="iactiononclrevent-interface"></a>IActionOnCLREvent, interface
Fournit la méthode [IActionOnCLREvent :: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) , qui exécute des rappels sur les événements qui ont été inscrits à l’aide d’un appel à la méthode [ICLROnEventManager :: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[OnEvent, méthode](iactiononclrevent-onevent-method.md)|Exécute un rappel pour un événement inscrit.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [EClrEvent, énumération](eclrevent-enumeration.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
- [ICLROnEventManager, interface](iclroneventmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
