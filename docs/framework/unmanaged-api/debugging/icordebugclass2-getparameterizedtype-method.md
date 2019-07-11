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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bfc503bfc2b278d7a7344b94cb089cd8e019890
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747763"
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
 [in] Une valeur de l’énumération CorElementType qui spécifie le type d’élément pour cette classe : Définissez cette valeur à ELEMENT_TYPE_VALUETYPE si ICorDebugClass2 représente un type valeur. Définissez cette valeur à ELEMENT_TYPE_CLASS si ce `ICorDebugClass2` représente un type complexe.  
  
 `nTypeArgs`  
 [in] Le nombre de paramètres de type, si le type est générique. Le nombre de paramètres de type (le cas échéant) doit correspondre au nombre requis par la classe.  
  
 `ppTypeArgs`  
 [in] Tableau de pointeurs, chacun pointant vers un objet de ICorDebugType qui représente un paramètre de type. Si la classe n’est pas générique, cette valeur est null.  
  
 `ppType`  
 [out] Un pointeur vers l’adresse d’un `ICorDebugType` objet qui représente la déclaration de type. Cet objet équivaut à un <xref:System.Type> objet dans le code managé.  
  
## <a name="remarks"></a>Notes  
 Si la classe est non générique, autrement dit, si elle n’a aucun paramètre de type, `GetParameterizedType` simplement Obtient l’objet de type de runtime correspondant à la classe. Le `elementType` paramètre doit être défini sur le type d’élément correct pour la classe : ELEMENT_TYPE_VALUETYPE si la classe est un type valeur ; Sinon, ELEMENT_TYPE_CLASS.  
  
 Si la classe accepte les paramètres de type (par exemple, `ArrayList<T>`), vous pouvez utiliser `GetParameterizedType` pour construire un objet de type pour un type instancié tel que `ArrayList<int>`.  
  
## <a name="background-information"></a>Informations générales  
 Dans les versions 1.0 et 1.1 du .NET Framework, tous les types dans les métadonnées peuvent être directement mappé à un type dans le processus en cours d’exécution. Par conséquent, un type de métadonnées et un type de runtime avaient une représentation unique dans le processus en cours d’exécution. Toutefois, un type générique dans les métadonnées peut correspondre à plusieurs instanciations différentes du type dans le processus en cours d’exécution. Par exemple, le type de métadonnées `SortedList<K,V>` peut mapper à `SortedList<String, EmployeeRecord>`, `SortedList<Int32, String>`, `SortedList<String,Array<Int32>>`, et ainsi de suite. Par conséquent, vous avez besoin d’un moyen de gérer l’instanciation de type.  
  
 Le .NET Framework version 2.0 introduit le `ICorDebugType` interface. Pour un type générique, un `ICorDebugClass` ou `ICorDebugClass2` objet représente le type non instancié (`SortedList<K,V>`) et un `ICorDebugType` objet représente les différents types instanciés. Étant donné un `ICorDebugClass` ou `ICorDebugClass2` de l’objet, vous pouvez créer un `ICorDebugType` objet pour toute instanciation en appelant le `ICorDebugClass2::GetParameterizedType` (méthode). Vous pouvez également créer un `ICorDebugType` objet pour un type simple, tels que Int32, ou pour un type non générique.  
  
 L’introduction de la `ICorDebugType` objet pour représenter la notion d’exécution d’un type a des répercussions tout au long de l’API. Fonctions qui prenaient précédemment un `ICorDebugClass` ou `ICorDebugClass2` objet ou même un `CorElementType` valeur sont généralisées pour prendre un `ICorDebugType` objet.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
