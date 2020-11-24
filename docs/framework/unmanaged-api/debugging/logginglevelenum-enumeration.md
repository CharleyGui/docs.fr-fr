---
title: LoggingLevelEnum, énumération
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
ms.openlocfilehash: 389edbeb746fbeaf60d88bf9ee2a3a0731822e55
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672004"
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum, énumération

Indique le niveau de gravité d'un message de description qui est écrit dans le journal des événements quand un thread managé consigne un événement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`LTraceLevel0`|Le message est un niveau de trace 0.|  
|`LTraceLevel1`|Le message est un niveau de trace 1.|  
|`LTraceLevel2`|Le message est un niveau de trace 2.|  
|`LTraceLevel3`|Le message est un niveau de trace 3.|  
|`LTraceLevel4`|Le message est un niveau de trace 4.|  
|`LStatusLevel0`|Le message est un niveau d’État 0.|  
|`LStatusLevel1`|Le message est un niveau d’État 1.|  
|`LStatusLevel2`|Le message est un niveau d’État 2.|  
|`LStatusLevel3`|Le message est au niveau d’État 3.|  
|`LStatusLevel4`|Le message a le niveau d’État 4.|  
|`LWarningLevel`|Le message est un niveau d’avertissement.|  
|`LErrorLevel`|Le message est un niveau d’erreur.|  
|`LPanicLevel`|Le message est un niveau de panique.|  
  
## <a name="remarks"></a>Remarques  

 Le common language runtime (CLR) appelle la méthode [ICorDebugManagedCallback :: LogMessage](icordebugmanagedcallback-logmessage-method.md) pour notifier au débogueur qu’un thread managé a consigné un événement. Le CLR passe une valeur de l' `LoggingLevelEnum` énumération pour indiquer le niveau de gravité du message que le thread managé a écrit dans le journal des événements.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Diagnostics.EventLog>
- [Énumérations de débogage](debugging-enumerations.md)
