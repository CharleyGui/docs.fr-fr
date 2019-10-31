---
title: CorDebugPlatform, énumération
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
ms.openlocfilehash: 5d66503487e1b997e2b8cc7d3d46e210a4dbbe05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132765"
---
# <a name="cordebugplatform-enumeration"></a>CorDebugPlatform, énumération
Fournit les valeurs de plateforme cible utilisées par la méthode [ICorDebugDataTarget :: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|CORDB_PLATFORM_WINDOWS_X86|La plateforme cible est Windows s'exécutant sur du matériel Intel x86.|  
|CORDB_PLATFORM_WINDOWS_AMD64|La plateforme cible est Windows 64 bits s'exécutant sur du matériel AMD64 ou Intel EM64T.|  
|CORDB_PLATFORM_WINDOWS_IA64|La plateforme cible est Windows 32 bits s'exécutant sur du matériel IA-64.|  
|CORDB_PLATFORM_MAC_PPC|La plateforme cible est le système d’exploitation Macintosh s’exécutant sur un matériel PowerPC.|  
|CORDB_PLATFORM_MAC_X86|La plateforme cible est le système d’exploitation Macintosh s’exécutant sur du matériel Intel x86.|  
|CORDB_PLATFORM_WINDOWS_ARM|La plateforme cible est le système d’exploitation Macintosh s’exécutant sur le matériel ARM Windows.|  
|CORDB_PLATFORM_MAC_AMD64|La plateforme cible est le système d’exploitation Macintosh s’exécutant sur du matériel AMD64.|  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 Les membres `CORDB_PLATFORM_WINDOWS_ARM` et `CORDB_PLATFORM_MAC_AMD64` sont disponibles dans .NET Framework 4.5.2 et ultérieur.  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
