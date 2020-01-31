---
title: CorDebugMappingResult, énumération
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
ms.openlocfilehash: 317dc2fe8403ae25949410423f1a28ad365caf6a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789306"
---
# <a name="cordebugmappingresult-enumeration"></a>CorDebugMappingResult, énumération
Fournit les détails sur la façon dont la valeur du pointeur d'instruction a été obtenue.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a>Members  
  
|Member|Description|  
|------------|-----------------|  
|`MAPPING_PROLOG`|Le code natif est dans le prologue, donc la valeur de l’adresse IP est 0.|  
|`MAPPING_EPILOG`|Le code natif se trouve dans un épilogue, donc la valeur de l’adresse IP est l’adresse de la dernière instruction de la méthode.|  
|`MAPPING_NO_INFO`|Aucune information de mappage n’étant disponible pour la méthode, la valeur de l’adresse IP est 0.|  
|`MAPPING_UNMAPPED_ADDRESS`|Bien qu’il existe des informations de mappage pour la méthode, l’adresse actuelle ne peut pas être mappée au code MSIL (Microsoft Intermediate Language). La valeur de l’adresse IP est 0.|  
|`MAPPING_EXACT`|Soit la méthode est mappée exactement au code MSIL, soit le frame a été interprété, donc la valeur de l’adresse IP est exacte.|  
|`MAPPING_APPROXIMATE`|La méthode a été correctement mappée, mais la valeur de l’adresse IP peut être approximative.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la méthode [ICorDebugILFrame :: GetIP](icordebugilframe-getip-method.md) pour obtenir la valeur du pointeur d’instruction.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
