---
title: EClrEvent, énumération
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: 388f0de26983f8bb876f40a527f60d8bc59191a3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616344"
---
# <a name="eclrevent-enumeration"></a>EClrEvent, énumération
Décrit les événements common language runtime (CLR) pour lesquels l’hôte peut inscrire des rappels.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`Event_ClrDisabled`|Spécifie une erreur CLR irrécupérable.|  
|`Event_DomainUnload`|Spécifie le déchargement d’un particulier <xref:System.AppDomain> .|  
|`Event_MDAFired`|Spécifie qu’un message de l’Assistant Débogage managé (MDA) a été généré.|  
|`Event_StackOverflow`|Spécifie qu’une erreur de dépassement de capacité de la pile s’est produite.|  
  
## <a name="remarks"></a>Notes  
 L’hôte peut enregistrer des rappels pour tous les types d’événements décrits par `EClrEvent` en appelant des méthodes de l’interface [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) . L’hôte obtient un pointeur vers cette interface en appelant la méthode [ICLRControl :: GetCLRManager](iclrcontrol-getclrmanager-method.md) .  
  
 Les `Event_CLRDisabled` `Event_DomainUnload` événements et peuvent être déclenchés plusieurs fois et à partir de différents threads pour signaler un déchargement ou la désactivation du CLR.  
  
 L' `Event_MDAFired` événement déclenche la création d’une instance [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) qui contient les détails du message de l’Assistant Débogage managé. Pour plus d’informations sur les MDA, consultez [diagnostic des erreurs avec les Assistants Débogage managé](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IActionOnCLREvent, interface](iactiononclrevent-interface.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
- [Énumérations d'hébergement](hosting-enumerations.md)
