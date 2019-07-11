---
title: USER_THREAD, structure
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0191f1fa17d436944fcb590d88dd4004adfa1aba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744303"
---
# <a name="userthread-structure"></a>USER_THREAD, structure
Fournit des informations à un débogueur sur un thread. Pour plus d’informations, consultez le [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`pSidBuffer`|Adresse de mémoire tampon de thread.|  
|`dwSidLen`|Longueur de la mémoire tampon de thread, en octets.|  
|`dwTid`|ID de thread.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Voir aussi

- [SetNotifyFilter, méthode](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [Structures du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
