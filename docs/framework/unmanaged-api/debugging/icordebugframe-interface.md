---
title: ICorDebugFrame, interface
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: ba138e79e0d6fb6f9c5e9c3efe3466f3c88cccae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782621"
---
# <a name="icordebugframe-interface"></a>ICorDebugFrame, interface

Représente un frame sur la pile en cours.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateStepper, méthode](icordebugframe-createstepper-method.md)|Obtient un ICorDebugStepper pour exécuter des opérations pas à pas relatives à cette `ICorDebugFrame`.|  
|[GetCallee, méthode](icordebugframe-getcallee-method.md)|Obtient un pointeur vers le `ICorDebugFrame` dans la chaîne actuelle appelée par ce frame, ou retourne null s’il s’agit du frame le plus profond dans la chaîne.|  
|[GetCaller, méthode](icordebugframe-getcaller-method.md)|Obtient un pointeur vers le `ICorDebugFrame` dans la chaîne actuelle qui a appelé ce frame, ou retourne la valeur null s’il s’agit du frame le plus à l’extérieur dans la chaîne.|  
|[GetChain, méthode](icordebugframe-getchain-method.md)|Obtient un pointeur vers l’ICorDebugChain auquel ce `ICorDebugFrame` fait partie.|  
|[GetCode, méthode](icordebugframe-getcode-method.md)|Obtient un pointeur vers le ICorDebugCode associé à ce frame de pile.|  
|[GetFunction, méthode](icordebugframe-getfunction-method.md)|Obtient un pointeur vers le ICorDebugFunction qui contient le code associé à ce frame de pile.|  
|[GetFunctionToken, méthode](icordebugframe-getfunctiontoken-method.md)|Obtient le jeton de métadonnées pour la fonction qui contient le code associé à ce frame de pile.|  
|[GetStackRange, méthode](icordebugframe-getstackrange-method.md)|Obtient la plage d’adresses absolues du frame de pile représenté par ce `ICorDebugFrame`.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
