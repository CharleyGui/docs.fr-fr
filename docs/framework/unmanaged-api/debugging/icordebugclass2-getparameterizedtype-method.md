---
title: ICorDebugClass2::GetParameterizedType, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.GetParameterizedType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::GetParameterizedType
helpviewer_keywords:
- GetParameterizedType method [.NET Framework debugging]
- ICorDebugClass2::GetParameterizedType method [.NET Framework debugging]
ms.assetid: 94b591c4-9302-4af2-a510-089496afb036
topic_type:
- apiref
ms.openlocfilehash: 64537ab97c1256cc6f963999b027bafc25cbbccb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125732"
---
# <a name="icordebugclass2getparameterizedtype-method"></a>ICorDebugClass2::GetParameterizedType, méthode
Obtient la déclaration de type pour cette classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetParameterizedType (  
    [in] CorElementType                      elementType,  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType  *ppTypeArgs[],  
    [out] ICorDebugType                    **ppType  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `elementType`  
 dans Valeur de l’énumération CorElementType qui spécifie le type d’élément de cette classe : définissez cette valeur sur ELEMENT_TYPE_VALUETYPE si ce ICorDebugClass2 représente un type valeur. Définissez cette valeur sur ELEMENT_TYPE_CLASS si cette `ICorDebugClass2` représente un type complexe.  
  
 `nTypeArgs`  
 dans Nombre de paramètres de type, si le type est générique. Le nombre de paramètres de type (le cas échéant) doit correspondre au nombre requis par la classe.  
  
 `ppTypeArgs`  
 dans Tableau de pointeurs, chacun pointant vers un objet ICorDebugType qui représente un paramètre de type. Si la classe n’est pas générique, cette valeur est null.  
  
 `ppType`  
 à Pointeur vers l’adresse d’un objet `ICorDebugType` qui représente la déclaration de type. Cet objet est équivalent à un objet <xref:System.Type> dans du code managé.  
  
## <a name="remarks"></a>Notes  
 Si la classe n’est pas générique, autrement dit, si elle n’a pas de paramètres de type, `GetParameterizedType` obtient simplement l’objet de type au moment de l’exécution correspondant à la classe. Le paramètre `elementType` doit être défini sur le type d’élément correct pour la classe : ELEMENT_TYPE_VALUETYPE si la classe est un type valeur ; dans le cas contraire, ELEMENT_TYPE_CLASS.  
  
 Si la classe accepte des paramètres de type (par exemple, `ArrayList<T>`), vous pouvez utiliser `GetParameterizedType` pour construire un objet de type pour un type instancié tel que `ArrayList<int>`.  
  
## <a name="background-information"></a>Informations générales  
 Dans les versions 1,0 et 1,1 de .NET Framework, chaque type dans les métadonnées peut être mappé directement à un type dans le processus en cours d’exécution. Ainsi, un type de métadonnées et un type de Runtime ont une représentation unique dans le processus en cours d’exécution. Toutefois, un type générique dans les métadonnées peut être mappé à de nombreuses instanciations différentes du type dans le processus en cours d’exécution. Par exemple, le type de métadonnées `SortedList<K,V>` peut mapper à `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, etc. Par conséquent, vous avez besoin d’un moyen de gérer l’instanciation de type.  
  
 La version 2,0 de .NET Framework introduit l’interface `ICorDebugType`. Pour un type générique, un objet `ICorDebugClass` ou `ICorDebugClass2` représente le type non instancié (`SortedList<K,V>`) et un objet `ICorDebugType` représente les différents types instanciés. À partir d’un objet `ICorDebugClass` ou `ICorDebugClass2`, vous pouvez créer un objet `ICorDebugType` pour toute instanciation en appelant la méthode `ICorDebugClass2::GetParameterizedType`. Vous pouvez également créer un objet `ICorDebugType` pour un type simple, tel que Int32, ou pour un type non générique.  
  
 L’introduction de l’objet `ICorDebugType` pour représenter la notion d’exécution d’un type a un effet ondulation sur l’ensemble de l’API. Les fonctions qui prenaient précédemment un objet `ICorDebugClass` ou `ICorDebugClass2` ou même une valeur `CorElementType` sont généralisées pour prendre un objet `ICorDebugType`.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
