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
ms.openlocfilehash: b9e488a512ad506a8975bfff44ae02cd84c29f74
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861695"
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
  
## <a name="parameters"></a>Parameters  
 `moduleID`  
 dans Identificateur du module dont les métadonnées ont été modifiées.  
  
## <a name="remarks"></a>Notes  
 Si des modifications de métadonnées sont apportées après le rappel [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) , vous devez appeler cette méthode avant d’utiliser les nouvelles métadonnées.  
  
 `ApplyMetaData` prend en charge uniquement l’ajout des types de métadonnées suivants :  
  
- `AssemblyRef` les enregistrements que vous créez en appelant [IMetaDataAssemblyEmit ::D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md). .  
  
- `TypeRef` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) .  
  
- `TypeSpec` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit :: GetTokenFromTypeSpec,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) .  
  
- `MemberRef` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) .  
  
- `MemberSpec` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit2 ::D efinemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) .  
  
- `UserString` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) .  

À compter de .NET Core 3,0, `ApplyMetaData` prend également en charge les types suivants :

- `TypeDef` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) .

- `MethodDef` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit ::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) . Toutefois, l’ajout de méthodes virtuelles à un type existant n’est pas pris en charge. Les méthodes virtuelles doivent être ajoutées avant le rappel de [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .

## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo7, interface](icorprofilerinfo7-interface.md)
