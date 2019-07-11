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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef142ed5284262fd758ff13af8207b2290938e77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741147"
---
# <a name="clrdebuggingprocessflags-enumeration"></a>CLR_DEBUGGING_PROCESS_FLAGS, énumération
Fournit des valeurs qui sont utilisées par le [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) (méthode).  
  
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
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|Ce runtime possède un événement de débogueur managé non-catch-up à envoyer. Consultez la section Notes pour la distinction entre les événements de mise à jour et non-catch-up.|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|L’événement géré qui est en attente est un <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> demande.|  
  
## <a name="remarks"></a>Notes  
 Les événements de mise à jour incluent des processus, ce domaine d’application, assembly, module et les notifications de la création du thread qui donnent le débogueur jusqu'à l’état actuel une fois qu’il a attaché à un processus. Les événements de non-catch-up, qui sont indiquées par le `CLR_DEBUGGING_MANAGED_EVENT_PENDING` indicateur, incluez tous les autres événements de débogueur, telles que les exceptions, puis gérés débogage notifications de l’assistant (MDA).  
  
 Le `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` indicateur permet au runtime de faire la distinction entre une exception de fin et une demande pour attacher un débogueur managé qui peut être annulé.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Metahost.idl, Metahost.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
