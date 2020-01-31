---
title: ICorDebugBreakpoint, interface
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
ms.openlocfilehash: 53d8d219a13f2dade16a338efccf0837f8de0158
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784375"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint, interface

Représente un point d’arrêt dans une fonction, ou un point de suivi sur une valeur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Activate, méthode](icordebugbreakpoint-activate-method.md)|Définit l’état actif de cette `ICorDebugBreakpoint`.|  
|[IsActive, méthode](icordebugbreakpoint-isactive-method.md)|Obtient une valeur qui indique si ce `ICorDebugBreakpoint` est actif.|  
  
## <a name="remarks"></a>Notes  
 Les points d’arrêt ne prennent pas directement en charge les expressions conditionnelles. Si de telles fonctionnalités sont souhaitées, un débogueur doit l’implémenter sur `ICorDebugBreakpoint`.  
  
 L’interface ICorDebugFunctionBreakpoint étend `ICorDebugBreakpoint` pour prendre en charge les points d’arrêt dans les fonctions.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
