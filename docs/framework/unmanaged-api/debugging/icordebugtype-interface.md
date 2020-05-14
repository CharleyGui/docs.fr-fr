---
title: ICorDebugType, interface
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
ms.openlocfilehash: 5e88652ff75223e30e6abc454f1e1af91494c7b2
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396704"
---
# <a name="icordebugtype-interface"></a>ICorDebugType, interface
Représente un type, de base ou complexe (autrement dit, défini par l’utilisateur). Si le type est générique, `ICorDebugType` représente le type générique instancié.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumerateTypeParameters, méthode](icordebugtype-enumeratetypeparameters-method.md)|Obtient un pointeur d’interface vers un ICorDebugTypeEnum qui référence les <xref:System.Type> paramètres génériques de la classe référencée par ce `ICorDebugType` .|  
|[GetBase, méthode](icordebugtype-getbase-method.md)|Obtient un pointeur d’interface vers un `ICorDebugType` qui référence la classe de base de la classe référencée par ce `ICorDebugType` , le cas échéant.|  
|[GetClass, méthode](icordebugtype-getclass-method.md)|Obtient un pointeur d’interface vers une ICorDebugClass qui référence le constructeur typé de ce `ICorDebugType` .|  
|[GetFirstTypeParameter, méthode](icordebugtype-getfirsttypeparameter-method.md)|Obtient un pointeur d’interface vers un `ICorDebugType` qui référence le premier <xref:System.Type> paramètre générique pour le constructeur de la classe référencée par ce `ICorDebugType` .|  
|[GetRank, méthode](icordebugtype-getrank-method.md)|Obtient le nombre de dimensions dans un type de tableau.|  
|[GetStaticFieldValue, méthode](icordebugtype-getstaticfieldvalue-method.md)|Obtient un pointeur d’interface vers un ICorDebugValue qui contient la valeur du champ statique référencé par le jeton de champ spécifié dans le frame de pile spécifié.|  
|[GetType, méthode](icordebugtype-gettype-method.md)|Obtient une valeur CorElementType qui décrit le type natif de la common language runtime <xref:System.Type> référencée par ce `ICorDebugType` .|  
  
## <a name="remarks"></a>Notes  
 Si le type est générique, `ICorDebugClass` représente le type non instancié. L' `ICorDebugType` interface représente un type générique instancié. Par exemple, Hashtable \< K, V> serait représenté par `ICorDebugClass` , alors que Hashtable \< Int32, String> serait représenté par `ICorDebugType` .  
  
 Les types non génériques sont représentés par `ICorDebugClass` et `ICorDebugType` . La dernière interface a été introduite dans la version 2,0 de .NET Framework pour gérer l’instanciation de type.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
