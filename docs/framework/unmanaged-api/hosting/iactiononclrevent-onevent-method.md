---
title: IActionOnCLREvent::OnEvent, méthode
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
ms.openlocfilehash: bbf5e299285071ba6d43fd2c40fc724d19bc7b2a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504353"
---
# <a name="iactiononclreventonevent-method"></a>IActionOnCLREvent::OnEvent, méthode
Exécute des rappels sur les événements qui ont été inscrits à l’aide d’un appel à la méthode [ICLROnEventManager :: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `event`  
 dans L’une des valeurs [EClrEvent](eclrevent-enumeration.md) , qui indique le type d’événement.  
  
 `data`  
 dans Pointeur vers un objet qui contient des détails sur `event` .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`OnEvent`retourné avec succès.|  
|HOST_E_CLRNOTAVAILABLE|Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.|  
|HOST_E_TIMEOUT|Le délai d’attente de l’appel a expiré.|  
|HOST_E_NOT_OWNER|L’appelant ne possède pas le verrou.|  
|HOST_E_ABANDONED|Un événement a été annulé alors qu’un thread ou une fibre bloqué attendait dessus.|  
|E_FAIL|Une défaillance catastrophique inconnue s’est produite. Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus. Les appels suivants à toute méthode d’hébergement retournent HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Remarques  
 Le `data` paramètre est un pointeur vers un objet de type non spécifié. Si le `event` paramètre a la valeur `Event_DomainUnload` , `data` est l’identificateur numérique pour le <xref:System.AppDomain> qui a été déchargé. L’hôte peut prendre les mesures appropriées à l’aide de cet identificateur comme clé.  
  
 Si `event` est `Event_MDAFired` , `data` est un pointeur vers une instance [MDAInfo](mdainfo-structure.md) qui contient la sortie de message d’un Assistant Débogage managé (MDA). Les MDA sont une fonctionnalité du CLR qui permet aux développeurs de déboguer, en générant des messages XML sur les événements qui, sinon, sont difficiles à intercepter. Ces messages peuvent être particulièrement utiles lors du débogage de transitions entre du code managé et du code non managé. Pour plus d’informations, consultez [diagnostic des erreurs avec les Assistants Débogage managé](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Diagnostic d’erreurs avec les Assistants Débogage managé](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [EClrEvent, énumération](eclrevent-enumeration.md)
- [IActionOnCLREvent, interface](iactiononclrevent-interface.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
- [ICLROnEventManager, interface](iclroneventmanager-interface.md)
- [MDAInfo, structure](mdainfo-structure.md)
