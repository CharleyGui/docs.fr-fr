---
title: ICorDebugThread::GetCurrentException, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
ms.openlocfilehash: c21be7b062b7e2d4129bafabae004351442ab853
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728054"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException, méthode

Obtient un pointeur d’interface vers un objet ICorDebugValue qui représente une exception actuellement levée par du code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppExceptionObject`  
 à Pointeur vers l’adresse d’un `ICorDebugValue` objet qui représente l’exception actuellement levée par le code managé.  
  
## <a name="remarks"></a>Remarques  

 L’objet exception existera à partir du moment où l’exception sera levée jusqu’à la fin du `catch` bloc. Une évaluation de fonction, qui est effectuée par les méthodes ICorDebugEval, supprime l’objet exception lors de l’installation et le restaure à la fin de l’opération.  
  
 Les exceptions peuvent être imbriquées (par exemple, si une exception est levée dans un filtre ou une évaluation de fonction), il peut donc y avoir plusieurs exceptions en suspens sur un seul thread. `GetCurrentException` retourne l’exception la plus récente.  
  
 L’objet et le type de l’exception peuvent changer tout au long de la durée de vie de l’exception. Par exemple, après la levée d’une exception de type x, le common language runtime (CLR) peut manquer de mémoire et le promouvoir en une exception de mémoire insuffisante.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
