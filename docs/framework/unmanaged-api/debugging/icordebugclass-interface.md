---
title: ICorDebugClass, interface
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
ms.openlocfilehash: d7417e8dc193172c77d23fe3fa72c8298d802b5c
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894040"
---
# <a name="icordebugclass-interface"></a>ICorDebugClass, interface

Représente un type, qui peut être de base ou complexe (c'est-à-dire défini par l'utilisateur). Si le type est générique, `ICorDebugClass` représente le type générique non instancié.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetModule, méthode](icordebugclass-getmodule-method.md)|Obtient le module qui définit cette classe.|  
|[GetStaticFieldValue, méthode](icordebugclass-getstaticfieldvalue-method.md)|Obtient la valeur du champ statique spécifié.|  
|[GetToken, méthode](icordebugclass-gettoken-method.md)|Obtient le `TypeDef` jeton de métadonnées pour cette classe.|  
  
## <a name="remarks"></a>Notes   
 L' `ICorDebugClass` interface représente un type générique non instancié. L’interface ICorDebugType représente un type générique instancié. Par exemple, `Hashtable<K, V>` serait représenté par `ICorDebugClass`, tandis `Hashtable<Int32, String>` que serait représenté par `ICorDebugType`.  
  
 Les `ICorDebugClass` types non génériques sont représentés par et `ICorDebugType`. La dernière interface a été introduite dans la version 2,0 de .NET Framework pour gérer l’instanciation de type.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
