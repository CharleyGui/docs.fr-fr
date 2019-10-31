---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, méthode
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 103fe1b6845edfe0a364db979557db63511f6ee3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130385"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, méthode

Retourne un énumérateur à toutes les méthodes définies dans un module NGen donné et incluse dans une méthode donnée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a>Paramètres

`inlinersModuleId`\
dans Identificateur d’un module NGen.

`inlineeModuleId`\
dans Identificateur d’un module qui définit `inlineeMethodId`. Pour plus d'informations, consultez la section Notes.

`inlineeMethodId`\
dans Identificateur d’une méthode Inline. Pour plus d'informations, consultez la section Notes.

`incompleteData`\
à Indicateur qui spécifie si `ppEnum` contient toutes les méthodes qui entourent une méthode donnée.  Pour plus d'informations, consultez la section Notes.

`ppEnum`\
à Pointeur vers l’adresse d’un énumérateur

## <a name="remarks"></a>Notes

`inlineeModuleId` et `inlineeMethodId` forment ensemble l’identificateur complet de la méthode qui peut être Inline. Par exemple, supposons que le module `A` définit une méthode `Simple.Add`:

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

et le module B définissent `Fancy.AddTwice`:

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

Laisse également supposer que `Fancy.AddTwice` Inline l’appel à `SimpleAdd`. Un profileur peut utiliser cet énumérateur pour rechercher toutes les méthodes définies dans le module B en ligne `Simple.Add`, et le résultat doit énumérer `AddTwice`.  `inlineeModuleId` est l’identificateur de module `A`et `inlineeMethodId` est l’identificateur de `Simple.Add(int a, int b)`.

Si `incompleteData` a la valeur true après le retour de la fonction, l’énumérateur ne contient pas toutes les méthodes qui entourent une méthode donnée. Cela peut se produire lorsqu’une ou plusieurs dépendances directes ou indirectes du module Inlines n’ont pas encore été chargées. Si un profileur a besoin de données précises, il doit réessayer plus tard lorsque d’autres modules sont chargés, de préférence lors du chargement de chaque module.

La méthode `EnumNgenModuleMethodsInliningThisMethod` peut être utilisée pour contourner les limitations relatives à l’incorporation de ReJIT. ReJIT permet à un profileur de modifier l’implémentation d’une méthode, puis de lui créer un nouveau code à la volée. Par exemple, nous pourrions modifier `Simple.Add` comme suit :

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

Toutefois, étant donné que `Fancy.AddTwice` a déjà inséré des `Simple.Add`, il continue d’avoir le même comportement qu’avant. Pour contourner cette limitation, l’appelant doit rechercher toutes les méthodes de tous les modules qui Inline `Simple.Add` et utiliser `ICorProfilerInfo5::RequestRejit` sur chacune de ces méthodes. Lorsque les méthodes sont recompilées, elles ont le nouveau comportement de `Simple.Add` au lieu de l’ancien comportement.

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions du .NET Framework :** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo6, interface](icorprofilerinfo6-interface.md)
