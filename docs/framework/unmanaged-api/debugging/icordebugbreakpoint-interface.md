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
ms.openlocfilehash: b92c3d3328c657762ed002155ef4947a9292b19e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894729"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint, interface

Représente un point d’arrêt dans une fonction, ou un point de suivi sur une valeur.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Activate, méthode](icordebugbreakpoint-activate-method.md)|Définit l’état actif de ce `ICorDebugBreakpoint`.|  
|[IsActive, méthode](icordebugbreakpoint-isactive-method.md)|Obtient une valeur qui indique si ce `ICorDebugBreakpoint` est actif.|  
  
## <a name="remarks"></a>Notes   
 Les points d’arrêt ne prennent pas directement en charge les expressions conditionnelles. Si de telles fonctionnalités sont souhaitées, un débogueur doit l’implémenter `ICorDebugBreakpoint`en plus de.  
  
 L’interface ICorDebugFunctionBreakpoint étend `ICorDebugBreakpoint` pour prendre en charge les points d’arrêt dans les fonctions.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
