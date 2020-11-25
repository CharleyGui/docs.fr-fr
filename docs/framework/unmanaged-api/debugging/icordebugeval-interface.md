---
title: ICorDebugEval, interface
ms.date: 03/30/2017
api_name:
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
ms.openlocfilehash: 5d8fd79b242f2b88b82c5c3d78dfe45d80f1194f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729783"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval, interface

Fournit des méthodes pour permettre au débogueur d'exécuter le code à l'intérieur du contexte du code en cours de débogage.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Abort, méthode](icordebugeval-abort-method.md)|Abandonne le calcul `ICorDebugEval` actuellement effectué par cet objet.|  
|[CallFunction, méthode](icordebugeval-callfunction-method.md)|Configure un appel à la fonction spécifiée. (Obsolète dans la .NET Framework version 2,0 ; utilisez [ICorDebugEval2 :: CallParameterizedFunction,](icordebugeval2-callparameterizedfunction-method.md) à la place.)|  
|[CreateValue, méthode](icordebugeval-createvalue-method.md)|Obtient un pointeur d’interface vers un objet « ICorDebugValue » du type spécifié, avec une valeur initiale de zéro ou null. (Obsolète dans la .NET Framework 2,0 ; utilisez [ICorDebugEval2 :: CreateValueForType,](icordebugeval2-createvaluefortype-method.md) à la place.)|  
|[GetResult, méthode](icordebugeval-getresult-method.md)|Obtient un pointeur d’interface vers un `ICorDebugValue` qui contient les résultats de l’évaluation.|  
|[GetThread, méthode](icordebugeval-getthread-method.md)|Obtient un pointeur d’interface vers le « ICorDebugThread » où cette évaluation est en cours d’exécution ou s’exécute.|  
|[IsActive, méthode](icordebugeval-isactive-method.md)|Obtient une valeur qui indique si cet `ICorDebugEval` objet est en cours d’exécution.|  
|[NewArray, méthode](icordebugeval-newarray-method.md)|Alloue un nouveau tableau du type d’élément et des dimensions spécifiés. (Obsolète dans la .NET Framework 2,0 ; utilisez [ICorDebugEval2 :: NewParameterizedArray,](icordebugeval2-newparameterizedarray-method.md) à la place.)|  
|[NewObject, méthode](icordebugeval-newobject-method.md)|Alloue une nouvelle instance d’objet et appelle la méthode de constructeur spécifiée. (Obsolète dans la .NET Framework 2,0 ; utilisez [ICorDebugEval2 :: NewParameterizedObject,](icordebugeval2-newparameterizedobject-method.md) à la place.)|  
|[NewObjectNoConstructor, méthode](icordebugeval-newobjectnoconstructor-method.md)|Alloue une nouvelle instance d’objet du type spécifié, sans tenter d’appeler une méthode de constructeur. (Obsolète dans la .NET Framework 2,0 ; utilisez [ICorDebugEval2 :: NewParameterizedObjectNoConstructor,](icordebugeval2-newparameterizedobjectnoconstructor-method.md) à la place.)|  
|[NewString, méthode](icordebugeval-newstring-method.md)|Alloue un nouvel objet String avec le contenu spécifié.|  
  
## <a name="remarks"></a>Remarques  

 Un `ICorDebugEval` objet est créé dans le contexte d’un thread spécifique qui est utilisé pour effectuer les évaluations. Tous les objets et types utilisés dans une évaluation donnée doivent se trouver dans le même domaine d’application. Ce domaine d’application n’a pas besoin d’être le même que le domaine d’application actuel du thread. Les évaluations peuvent être imbriquées.  
  
 Les opérations de l’évaluation ne se terminent pas tant que le débogueur n’a pas appelé [ICorDebugController :: continue](icordebugcontroller-continue-method.md), puis reçoit un rappel [ICorDebugManagedCallback :: EvalComplete,](icordebugmanagedcallback-evalcomplete-method.md) . Si vous devez utiliser la fonctionnalité d’évaluation sans permettre à d’autres threads de s’exécuter, interrompez les threads à l’aide de [ICorDebugController :: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) ou [ICorDebugController :: Stop](icordebugcontroller-stop-method.md) avant d’appeler [ICorDebugController :: continue](icordebugcontroller-continue-method.md).  
  
 Étant donné que le code utilisateur s’exécute lorsque l’évaluation est en cours, tous les événements de débogage peuvent se produire, y compris les charges de classe et les points d’arrêt. Le débogueur recevra des rappels, comme d’habitude, pour ces événements. L’état de l’évaluation sera visible dans le cadre de l’inspection de l’état normal du programme. La chaîne de pile sera une `CHAIN_FUNC_EVAL` chaîne (consultez l’énumération « CorDebugStepReason, » et la méthode [ICorDebugChain :: GetReason](icordebugchain-getreason-method.md) ). L’API du débogueur complet continue à fonctionner normalement.  
  
 Si une situation de boucle incomplète ou infinie se produit, le code utilisateur peut ne jamais se terminer. Dans ce cas, vous devez appeler [ICorDebugEval :: Abort](icordebugeval-abort-method.md) avant de reprendre le programme.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
