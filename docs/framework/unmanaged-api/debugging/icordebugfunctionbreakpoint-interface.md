---
title: ICorDebugFunctionBreakpoint, interface
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint
helpviewer_keywords:
- ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type:
- apiref
ms.openlocfilehash: 6a378e3579ab9ea8d9534a408d0e456373616cad
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213136"
---
# <a name="icordebugfunctionbreakpoint-interface"></a>ICorDebugFunctionBreakpoint, interface

Étend l’interface ICorDebugBreakpoint pour prendre en charge les points d’arrêt dans les fonctions.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetFunction, méthode](icordebugfunctionbreakpoint-getfunction-method.md)|Obtient un pointeur d’interface vers un ICorDebugFunction qui fait référence à la fonction dans laquelle le point d’arrêt est défini.|  
|[GetOffset, méthode](icordebugfunctionbreakpoint-getoffset-method.md)|Obtient l’offset du point d’arrêt dans la fonction.|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
