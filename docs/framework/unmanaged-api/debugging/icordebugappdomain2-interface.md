---
title: ICorDebugAppDomain2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
ms.openlocfilehash: 1643d91f373ff233540026440ee21aa4c146f3e3
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895137"
---
# <a name="icordebugappdomain2-interface"></a>ICorDebugAppDomain2, interface

Fournit des méthodes pour utiliser des tableaux, des pointeurs, des pointeurs de fonction et des types référence. Cette interface est une extension de l’interface ICorDebugAppDomain.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetArrayOrPointerType, méthode](icordebugappdomain2-getarrayorpointertype-method.md)|Obtient un tableau du type spécifié, ou un pointeur ou une référence au type spécifié.|  
|[GetFunctionPointerType](icordebugappdomain2-getfunctionpointertype-method.md)|Obtient un pointeur vers une fonction qui a une signature donnée.|  
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
