---
title: CorDebugMDAFlags, énumération
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
ms.openlocfilehash: e024500ea66dcb42e712e07e976a709401160a27
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795766"
---
# <a name="cordebugmdaflags-enumeration"></a>CorDebugMDAFlags, énumération
Spécifie l'état du thread sur lequel l'Assistant Débogage managé est déclenché.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|Le thread sur lequel l’Assistant Débogage managé a été déclenché a glissé depuis le déclenchement de l’Assistant Débogage managé.|  
  
## <a name="remarks"></a>Notes   
 Lorsque la pile des appels ne décrit plus où l’Assistant Débogage managé a été déclenché à l’origine, le thread est considéré comme ayant *glissé*. Il s’agit d’une circonstance inhabituelle résultant de l’exécution par le thread d’une opération non valide lors de la sortie.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
