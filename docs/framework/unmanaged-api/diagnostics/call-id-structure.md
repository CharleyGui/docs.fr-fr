---
title: CALL_ID, structure
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
ms.openlocfilehash: 3f41dd969e25f7a42308ff0b7b2d617344284b38
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725246"
---
# <a name="call_id-structure"></a>CALL_ID, structure

Fournit des informations à un débogueur sur une fonction qui est appelée. Pour plus d’informations, consultez l’interface [INotifySink2](inotifysink2-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`szMachine`|Identifie l’ordinateur qui effectue l’appel.|  
|`dwPid`|Identifie le processeur de l’ordinateur.|  
|`pUserThread`|Identifie le thread qui exécute l’appel.|  
|`addrStackPointer`|Spécifie l’adresse de la pile des appels.|  
|`szEntryPoint`|Spécifie l’adresse de l’appel.|  
|`szDestinationMachine`|Identifie l’ordinateur qui exécutera l’appel.|  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Voir aussi

- [INotifySink2, interface](inotifysink2-interface.md)
- [Structures du magasin de symboles de diagnostics](diagnostics-symbol-store-structures.md)
