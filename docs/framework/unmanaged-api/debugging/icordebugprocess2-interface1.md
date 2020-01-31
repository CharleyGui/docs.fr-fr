---
title: ICorDebugProcess2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
ms.openlocfilehash: 1ef6af11851acbe0f7e9469c9432ff09f9228608
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792505"
---
# <a name="icordebugprocess2-interface"></a>ICorDebugProcess2, interface
Extension logique de l’interface ICorDebugProcess, qui représente un processus exécutant du code managé.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint, méthode](icordebugprocess2-clearunmanagedbreakpoint-method.md)|Supprime un point d’arrêt au niveau de l’offset spécifié qui a été défini par un appel antérieur à `ICorDebugProcess2::SetUnmanagedBreakpoint`.|  
|[GetDesiredNGENCompilerFlags, méthode](icordebugprocess2-getdesiredngencompilerflags-method.md)|Obtient les indicateurs qui doivent être définis pour le common language runtime (CLR) pour charger l’image dans le processus référencé par cet `ICorDebugProcess2`.|  
|[GetReferenceValueFromGCHandle, méthode](icordebugprocess2-getreferencevaluefromgchandle-method.md)|Obtient un pointeur de référence vers l’objet managé spécifié qui a un handle de garbage collection.|  
|[GetThreadForTaskID, méthode](icordebugprocess2-getthreadfortaskid-method.md)|Obtient le thread sur lequel s’exécute la tâche avec l’identificateur spécifié.|  
|[GetVersion, méthode](icordebugprocess2-getversion-method.md)|Obtient la version du CLR sur laquelle le processus en cours de débogage est en cours d’exécution.|  
|[SetDesiredNGENCompilerFlags, méthode](icordebugprocess2-setdesiredngencompilerflags-method.md)|Définit les indicateurs requis pour que le compilateur juste-à-temps (JIT) charge une image dans le processus en cours de débogage.|  
|[SetUnmanagedBreakpoint, méthode](icordebugprocess2-setunmanagedbreakpoint-method.md)|Définit un point d’arrêt non managé au niveau de l’offset d’image native spécifié.|  
  
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
