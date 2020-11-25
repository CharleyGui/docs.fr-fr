---
title: ICorDebugAssembly, interface
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
ms.openlocfilehash: 821eae8ea5b4147408e9fe60d1e5b70c7936959e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696243"
---
# <a name="icordebugassembly-interface"></a>ICorDebugAssembly, interface

Représente un assembly.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumerateModules, méthode](icordebugassembly-enumeratemodules-method.md)|Obtient un énumérateur pour les modules contenus dans l’assembly.|  
|[GetAppDomain, méthode](icordebugassembly-getappdomain-method.md)|Obtient un pointeur d’interface vers le domaine d’application qui contient cette `ICorDebugAssembly` instance.|  
|[GetCodeBase, méthode](icordebugassembly-getcodebase-method.md)|Non implémenté dans la version actuelle du .NET Framework.|  
|[GetName, méthode](icordebugassembly-getname-method.md)|Obtient le nom de l'assembly.|  
|[GetProcess, méthode](icordebugassembly-getprocess-method.md)|Obtient l’instance ICorDebugProcess dans laquelle l’assembly est en cours d’exécution.|  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
