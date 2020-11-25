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
ms.openlocfilehash: 409651aa69e957418ad46f61e1bd57add0eb10a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722893"
---
# <a name="user_thread-structure"></a>USER_THREAD, structure

Fournit des informations à un débogueur à propos d’un thread. Pour plus d’informations, consultez la méthode [INotifySource2 :: SetNotifyFilter,](inotifysource2-setnotifyfilter-method.md) .  
  
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
|`pSidBuffer`|Adresse de la mémoire tampon de thread.|  
|`dwSidLen`|Longueur de la mémoire tampon de thread, en octets.|  
|`dwTid`|ID de thread.|  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Voir aussi

- [SetNotifyFilter, méthode](inotifysource2-setnotifyfilter-method.md)
- [Structures du magasin de symboles de diagnostics](diagnostics-symbol-store-structures.md)
