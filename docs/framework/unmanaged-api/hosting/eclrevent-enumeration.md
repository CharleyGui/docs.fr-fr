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
ms.openlocfilehash: 5d6ec42da60a7b294177063b9f8bd5afbf352c62
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726819"
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
  
## <a name="remarks"></a>Remarques  

 L’hôte peut enregistrer des rappels pour tous les types d’événements décrits par `EClrEvent` en appelant des méthodes de l’interface [ICLROnEventManager](iclroneventmanager-interface.md) . L’hôte obtient un pointeur vers cette interface en appelant la méthode [ICLRControl :: GetCLRManager](iclrcontrol-getclrmanager-method.md) .  
  
 Les `Event_CLRDisabled` `Event_DomainUnload` événements et peuvent être déclenchés plusieurs fois et à partir de différents threads pour signaler un déchargement ou la désactivation du CLR.  
  
 L' `Event_MDAFired` événement déclenche la création d’une instance [MDAInfo](mdainfo-structure.md) qui contient les détails du message de l’Assistant Débogage managé. Pour plus d’informations sur les MDA, consultez [diagnostic des erreurs avec les Assistants Débogage managé](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IActionOnCLREvent, interface](iactiononclrevent-interface.md)
- [ICLRControl, interface](iclrcontrol-interface.md)
- [Énumérations d'hébergement](hosting-enumerations.md)
