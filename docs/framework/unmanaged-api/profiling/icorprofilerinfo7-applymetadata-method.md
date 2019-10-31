---
title: 'ICorProfilerInfo7 :: ApplyMetaData, méthode'
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
ms.openlocfilehash: 00d9bef1e2b59a2d2207d1e343380e0e81bee848
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130351"
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7 :: ApplyMetaData, méthode
[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]  
  
 Applique les métadonnées nouvellement définies par les méthodes `IMetadataEmit::Define*` à un module spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `moduleID`  
 dans Identificateur du module dont les métadonnées ont été modifiées.  
  
## <a name="remarks"></a>Notes  
 Si des modifications de métadonnées sont apportées après le rappel [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) , vous devez appeler cette méthode avant d’utiliser les nouvelles métadonnées.  
  
 `ApplyMetaData` prend en charge uniquement l’ajout des types de métadonnées suivants :  
  
- `AssemblyRef` les enregistrements que vous créez en appelant [IMetaDataAssemblyEmit ::D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md). .  
  
- `TypeRef` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) .  
  
- `TypeSpec` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit :: GetTokenFromTypeSpec,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) .  
  
- `MemberRef` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) .  
  
- `MemberSpec` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit2 ::D efinemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) .  
  
- `UserString` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) .  

À compter de .NET Core 3,0, `ApplyMetaData` prend également en charge les types suivants :

- `TypeDef` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) .

- `MethodDef` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) . Toutefois, l’ajout de méthodes virtuelles à un type existant n’est pas pris en charge. Les méthodes virtuelles doivent être ajoutées avant le rappel de [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) .

## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo7, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
