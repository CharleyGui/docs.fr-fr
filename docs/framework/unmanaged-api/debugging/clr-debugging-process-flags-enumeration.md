---
title: CLR_DEBUGGING_PROCESS_FLAGS, énumération
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
ms.openlocfilehash: dd148d23d6e29f03052d3bbf1fcd5d02fb332a0a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729848"
---
# <a name="clr_debugging_process_flags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS, énumération

Fournit des valeurs utilisées par la méthode [ICLRDebugging :: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|Ce runtime a un événement de débogueur géré non intercepté à envoyer. Consultez la section Notes pour la distinction entre les événements de rattrapage et de non-rattrapage.|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|L’événement managé qui est en attente est une <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> demande.|  
  
## <a name="remarks"></a>Remarques  

 Les événements de rattrapage incluent les notifications de processus, de domaine d’application, d’assembly, de module et de création de thread qui mettent le débogueur à l’état actuel une fois qu’il est attaché à un processus. Les événements de non-rattrapage, qui sont indiqués par l' `CLR_DEBUGGING_MANAGED_EVENT_PENDING` indicateur, incluent tous les autres événements du débogueur, tels que les exceptions et les notifications de l’Assistant Débogage managé (MDA).  
  
 L' `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` indicateur permet au runtime de faire la différence entre une exception d’arrêt et une demande d’attachement d’un débogueur managé qui peut être annulé.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Metahost. idl, Metahost. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
- [Débogage](index.md)
