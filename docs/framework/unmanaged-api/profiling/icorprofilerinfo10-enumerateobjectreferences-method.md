---
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: d6518612c213d21c2dc7d80878121ccd3b7e2abb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449855"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a>ICorProfilerInfo10 :: EnumerateObjectReferences, méthode

À partir d’un ObjectID, callback et ClientData :, énumère chaque référence d’objet (le cas échéant).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

#### <a name="parameters"></a>Paramètres

`objectId` \
dans Objet sur lequel énumérer les références.

`callback` \
dans Fonction qui sera appelée avec les références pour l’objet.

`clientData` \
dans Données fournies par le profileur à passer à la fonction `callback`.

## <a name="remarks"></a>Notes

La méthode `EnumerateObjectReferences` est semblable à [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), à ceci près qu’elle parcourt les références à la demande pour le profileur au lieu de préallouer un tableau pour stocker les références.

## <a name="requirements"></a>Configuration requise

**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**En-tête :** CorProf.idl, CorProf.h

**Bibliothèque :** CorGuids.lib

**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo10](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
