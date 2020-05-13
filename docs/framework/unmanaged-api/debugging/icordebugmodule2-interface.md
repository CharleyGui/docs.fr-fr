---
title: ICorDebugModule2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
ms.openlocfilehash: 7b98302985d9d54599ea8ea2e01dc2503c468d58
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210226"
---
# <a name="icordebugmodule2-interface"></a>ICorDebugModule2, interface

Sert d’extension logique à l’interface ICorDebugModule.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ApplyChanges, méthode](icordebugmodule2-applychanges-method.md)|Applique les modifications apportées aux métadonnées et les modifications apportées au code MSIL (Microsoft Intermediate Language) au processus en cours d’exécution.|  
|[GetJITCompilerFlags, méthode](icordebugmodule2-getjitcompilerflags-method.md)|Obtient les indicateurs qui contrôlent la compilation juste-à-temps (JIT, Just-in-Time) pour ce `ICorDebugModule2` .|  
|[ResolveAssembly, méthode](icordebugmodule2-resolveassembly-method.md)|Résout l’assembly référencé par le jeton de métadonnées spécifié.|  
|[SetJITCompilerFlags, méthode](icordebugmodule2-setjitcompilerflags-method.md)|Définit les indicateurs qui contrôlent la compilation JIT pour ce `ICorDebugModule2` .|  
|[SetJMCStatus, méthode](icordebugmodule2-setjmcstatus-method.md)|Affecte la valeur spécifiée à l’état Uniquement mon code (uniquement mon code) de toutes les méthodes de toutes les classes de ce, à l' `ICorDebugModule2` exception de celles du `pTokens` tableau, qu’il définit sur la valeur opposée.|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
