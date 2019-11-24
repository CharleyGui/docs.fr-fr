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
ms.openlocfilehash: 8c606f67766334800444f39b115d90f65ecca13d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448598"
---
# <a name="call_id-structure"></a>CALL_ID, structure
Provides information to a debugger about a function that is being called. See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.  
  
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
|`szMachine`|Identifies the machine that is making the call.|  
|`dwPid`|Identifies the machine processor.|  
|`pUserThread`|Identifies the thread that is executing the call.|  
|`addrStackPointer`|Specifies the address of the call stack.|  
|`szEntryPoint`|Specifies the address of the call.|  
|`szDestinationMachine`|Identifies the machine that will execute the call.|  
  
## <a name="requirements"></a>spécifications  
 **Header:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Voir aussi

- [INotifySink2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [Structures du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
