---
title: ICorDebugController::EnumerateThreads, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
ms.openlocfilehash: 815dc63a2dedecc613506b0f98702f58d6e7bd04
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783788"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a>ICorDebugController::EnumerateThreads, méthode
Obtient un énumérateur pour les threads managés actifs dans le processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `ppThreads`  
 à Pointeur vers l’adresse d’un objet « ICorDebugThreadEnum » qui représente un énumérateur pour tous les threads managés qui sont actifs dans le processus.  
  
## <a name="remarks"></a>Notes  
 Un thread est considéré comme actif après la distribution du rappel [ICorDebugManagedCallback :: CreateThread](icordebugmanagedcallback-createthread-method.md) et avant la distribution du rappel [ICorDebugManagedCallback :: ExitThread](icordebugmanagedcallback-exitthread-method.md) . Un thread managé ne peut pas nécessairement avoir des frames managés sur sa pile. Les threads peuvent être énumérés avant même le rappel [ICorDebugManagedCallback :: CreateProcess](icordebugmanagedcallback-createprocess-method.md) . L’énumération est naturellement vide.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi
