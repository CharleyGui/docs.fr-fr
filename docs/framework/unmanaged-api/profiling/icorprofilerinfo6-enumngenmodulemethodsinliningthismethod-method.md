---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod, méthode
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 8ed3f305deceacb976aeff994db1588f9e1ce1fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495526"
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
dans Identificateur d’un module qui définit `inlineeMethodId` . Pour plus d'informations, consultez la section Remarques.

`inlineeMethodId`\
dans Identificateur d’une méthode Inline. Pour plus d'informations, consultez la section Remarques.

`incompleteData`\
à Indicateur qui signale si `ppEnum` contient toutes les méthodes incorporant une méthode donnée.  Pour plus d'informations, consultez la section Remarques.

`ppEnum`\
à Pointeur vers l’adresse d’un énumérateur

## <a name="remarks"></a>Remarques

`inlineeModuleId`et `inlineeMethodId` forment ensemble l’identificateur complet de la méthode qui peut être Inline. Par exemple, supposons que module `A` définit une méthode `Simple.Add` :

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

et le module B définit `Fancy.AddTwice` :

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

Laisse également supposer que `Fancy.AddTwice` l’appel à est inline `SimpleAdd` . Un profileur peut utiliser cet énumérateur pour rechercher toutes les méthodes définies dans le module B en ligne `Simple.Add` , et le résultat doit être énuméré `AddTwice` .  `inlineeModuleId`est l’identificateur du module `A` et `inlineeMethodId` est l’identificateur de `Simple.Add(int a, int b)` .

Si `incompleteData` a la valeur true après le retour de la fonction, l’énumérateur ne contient pas toutes les méthodes qui entourent une méthode donnée. Cela peut se produire lorsqu’une ou plusieurs dépendances directes ou indirectes du module Inlines n’ont pas encore été chargées. Si un profileur a besoin de données précises, il doit réessayer plus tard lorsque d’autres modules sont chargés, de préférence lors du chargement de chaque module.

La `EnumNgenModuleMethodsInliningThisMethod` méthode peut être utilisée pour contourner les limitations relatives à l’incorporation de ReJIT. ReJIT permet à un profileur de modifier l’implémentation d’une méthode, puis de lui créer un nouveau code à la volée. Par exemple, nous pourrions modifier `Simple.Add` les éléments suivants :

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

Toutefois, étant donné que `Fancy.AddTwice` a déjà été inclus `Simple.Add` , il continue à avoir le même comportement qu’avant. Pour contourner cette limitation, l’appelant doit rechercher toutes les méthodes de tous les modules qui sont inline `Simple.Add` et utilisent `ICorProfilerInfo5::RequestRejit` sur chacune de ces méthodes. Lorsque les méthodes sont recompilées, elles ont le nouveau comportement de `Simple.Add` au lieu de l’ancien comportement.

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions de .NET Framework :**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo6, interface](icorprofilerinfo6-interface.md)
