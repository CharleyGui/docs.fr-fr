---
title: ICorDebugEval2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
ms.openlocfilehash: e69b32430651edd0222db874e2659bd959f89549
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788707"
---
# <a name="icordebugeval2-interface"></a>ICorDebugEval2, interface

Étend « ICorDebugEval » pour assurer la prise en charge des types génériques.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CallParameterizedFunction, méthode](icordebugeval2-callparameterizedfunction-method.md)|Configure un appel au « ICorDebugFunction » spécifié, qui peut être imbriqué dans un type dont le constructeur prend des paramètres de type ou qui peut lui-même prendre des paramètres de type.|  
|[CreateValueForType, méthode](icordebugeval2-createvaluefortype-method.md)|Obtient un pointeur vers un nouveau « ICorDebugValue » du type spécifié, avec une valeur initiale de null ou zéro.|  
|[NewParameterizedArray, méthode](icordebugeval2-newparameterizedarray-method.md)|Alloue un nouveau tableau du type d’élément et des dimensions spécifiés.|  
|[NewParameterizedObject, méthode](icordebugeval2-newparameterizedobject-method.md)|Instancie un nouvel objet de type paramétré et appelle la méthode de constructeur de l’objet.|  
|[NewParameterizedObjectNoConstructor, méthode](icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Instancie un nouvel objet de type paramétrable de la classe spécifiée sans tenter d’appeler une méthode de constructeur|  
|[NewStringWithLength, méthode](icordebugeval2-newstringwithlength-method.md)|Crée une nouvelle chaîne de la longueur spécifiée avec le contenu spécifié.|  
|[RudeAbort, méthode](icordebugeval2-rudeabort-method.md)|Abandonne le calcul que ce `ICorDebugEval2` est en cours d’exécution.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
