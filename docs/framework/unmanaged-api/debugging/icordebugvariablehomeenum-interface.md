---
title: ICorDebugVariableHomeEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: d5962de8cc2762f6ecf4864c5255da0fe83918e4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396531"
---
# <a name="icordebugvariablehomeenum-interface"></a>ICorDebugVariableHomeEnum, interface
Fournit un énumérateur aux variables locales et aux arguments dans une fonction.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next, méthode](icordebugvariablehomeenum-next-method.md)|Obtient le nombre spécifié d’instances [ICorDebugVariableHome](icordebugvariablehome-interface.md) qui contiennent des informations sur les variables locales et les arguments d’une fonction.|  
  
## <a name="remarks"></a>Notes  
 L' `ICorDebugVariableHomeEnum` interface implémente l’interface ICorDebugEnum.  
  
 Une `ICorDebugVariableHomeEnum` instance est remplie avec des instances [ICorDebugVariableHome](icordebugvariablehome-interface.md) en appelant la méthode [ICorDebugCode4 :: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) . Chaque instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) de la collection représente une variable locale ou un argument dans une fonction. Les objets [ICorDebugVariableHome](icordebugvariablehome-interface.md) de la collection peuvent être énumérés en appelant la méthode [ICorDebugVariableHomeEnum :: Next](icordebugvariablehomeenum-next-method.md) .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugVariableHome, interface](icordebugvariablehome-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
