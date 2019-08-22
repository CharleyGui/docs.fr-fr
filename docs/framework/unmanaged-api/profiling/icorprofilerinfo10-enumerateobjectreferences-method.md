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
ms.openlocfilehash: ac193b6b78434245b8f11a4f627b4e1992feb8a7
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661271"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a>ICorProfilerInfo10:: EnumerateObjectReferences, méthode

À partir d’un ObjectID, callback et ClientData:, énumère chaque référence d’objet (le cas échéant).

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
dans Données fournies par le profileur à passer `callback` à la fonction.

## <a name="remarks"></a>Notes

La `EnumerateObjectReferences` méthode est similaire à [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), à ceci près qu’elle parcourt les références à la demande pour le profileur au lieu de préallouer un tableau pour stocker les références.

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).

**En-tête :** CorProf. idl, CorProf. h

**Bibliothèque** CorGuids.lib

**Versions de .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interface ICorProfilerInfo10](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
