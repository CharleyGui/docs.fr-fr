---
title: CorDebugRecordFormat, énumération
ms.date: 03/30/2017
api_name:
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
ms.openlocfilehash: cfbd856c73ab10642a7cf7c16cfb2d70e7fe9756
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795727"
---
# <a name="cordebugrecordformat-enumeration"></a>CorDebugRecordFormat, énumération
Décrit le format des données dans un tableau d'octets qui contient des informations sur un événement de débogage d'exception native.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|Les données correspondent à un enregistrement d'exception Windows 32 bits.|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|Les données correspondent à un enregistrement d'exception Windows 64 bits.|  
  
## <a name="remarks"></a>Notes   
 Un membre de l' `CorDebugRecordFormat` énumération est passé à la méthode [DecodeEvent](icordebugprocess6-decodeevent-method.md) pour indiquer le format du tableau d’octets dans `pRecord` son argument.  
  
> [!NOTE]
> Cette énumération est destinée à une utilisation dans des scénarios de débogage .NET Native uniquement.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
