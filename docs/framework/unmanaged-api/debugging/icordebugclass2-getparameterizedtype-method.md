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
ms.openlocfilehash: 329bcee441b395982a8a8b539c0a938fa8170b14
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894055"
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
 dans Valeur de l’énumération CorElementType qui spécifie le type d’élément de cette classe : définissez cette valeur sur ELEMENT_TYPE_VALUETYPE si ce ICorDebugClass2 représente un type valeur. Définissez cette valeur sur ELEMENT_TYPE_CLASS si ce `ICorDebugClass2` représente un type complexe.  
  
 `nTypeArgs`  
 dans Nombre de paramètres de type, si le type est générique. Le nombre de paramètres de type (le cas échéant) doit correspondre au nombre requis par la classe.  
  
 `ppTypeArgs`  
 dans Tableau de pointeurs, chacun pointant vers un objet ICorDebugType qui représente un paramètre de type. Si la classe n’est pas générique, cette valeur est null.  
  
 `ppType`  
 à Pointeur vers l’adresse d’un `ICorDebugType` objet qui représente la déclaration de type. Cet objet est équivalent à un <xref:System.Type> objet dans du code managé.  
  
## <a name="remarks"></a>Notes   
 Si la classe n’est pas générique, autrement dit, si elle n’a pas de paramètres `GetParameterizedType` de type, obtient simplement l’objet de type au moment de l’exécution correspondant à la classe. Le `elementType` paramètre doit être défini sur le type d’élément correct pour la classe : ELEMENT_TYPE_VALUETYPE si la classe est un type valeur ; Sinon, ELEMENT_TYPE_CLASS.  
  
 Si la classe accepte des paramètres de type (par `ArrayList<T>`exemple,), vous `GetParameterizedType` pouvez utiliser pour construire un objet de type pour un type instancié `ArrayList<int>`tel que.  
  
## <a name="background-information"></a>Informations générales  
 Dans les versions 1,0 et 1,1 de .NET Framework, chaque type dans les métadonnées peut être mappé directement à un type dans le processus en cours d’exécution. Ainsi, un type de métadonnées et un type de Runtime ont une représentation unique dans le processus en cours d’exécution. Toutefois, un type générique dans les métadonnées peut être mappé à de nombreuses instanciations différentes du type dans le processus en cours d’exécution. Par exemple `SortedList<K,V>` , le type de métadonnées peut `SortedList<String, EmployeeRecord>`être `SortedList<Int32, String>`mappé `SortedList<String,Array<Int32>>`à,,, etc. Par conséquent, vous avez besoin d’un moyen de gérer l’instanciation de type.  
  
 La version de .NET Framework 2,0 introduit `ICorDebugType` l’interface. Pour un type générique, un `ICorDebugClass` objet `ICorDebugClass2` ou représente le type non instancié (`SortedList<K,V>`) et un `ICorDebugType` objet représente les différents types instanciés. À partir `ICorDebugClass` d' `ICorDebugClass2` un objet ou, vous pouvez `ICorDebugType` créer un objet pour toute instanciation `ICorDebugClass2::GetParameterizedType` en appelant la méthode. Vous pouvez également créer un `ICorDebugType` objet pour un type simple, tel que Int32, ou pour un type non générique.  
  
 L’introduction de l' `ICorDebugType` objet pour représenter la notion d’exécution d’un type a un effet ondulation sur l’ensemble de l’API. Les fonctions qui prenaient précédemment `ICorDebugClass` un `ICorDebugClass2` objet ou, ou `CorElementType` même une valeur, sont généralisées `ICorDebugType` pour prendre un objet.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
