---
title: ICorDebugProcess::ThreadForFiberCookie, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ThreadForFiberCookie
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ThreadForFiberCookie
helpviewer_keywords:
- ICorDebugProcess::ThreadForFiberCookie method [.NET Framework debugging]
- ThreadForFiberCookie method [.NET Framework debugging]
ms.assetid: afe4e97f-bffc-47e1-adad-d6e842487f35
topic_type:
- apiref
ms.openlocfilehash: faaa118fa73a4c9b8750752d84a9dd980170ff66
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210447"
---
# <a name="icordebugprocessthreadforfibercookie-method"></a>ICorDebugProcess::ThreadForFiberCookie, méthode
Cette méthode n’est pas implémentée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ThreadForFiberCookie (  
    [in] DWORD fiberCookie,  
    [out] ICorDebugThread **ppThread  
);  
```  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
