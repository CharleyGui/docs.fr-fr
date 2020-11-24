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
ms.openlocfilehash: 2c71db25422740880d8b29576eff247d5eba5f1d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686109"
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7 :: ApplyMetaData, méthode

[Prise en charge dans le .NET Framework 4.6.1 et versions ultérieures]  
  
 Applique les métadonnées nouvellement définies par les `IMetadataEmit::Define*` méthodes à un module spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `moduleID`  
 dans Identificateur du module dont les métadonnées ont été modifiées.  
  
## <a name="remarks"></a>Remarques  

 Si des modifications de métadonnées sont apportées après le rappel [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) , vous devez appeler cette méthode avant d’utiliser les nouvelles métadonnées.  
  
 `ApplyMetaData` prend uniquement en charge l’ajout des types de métadonnées suivants :  
  
- `AssemblyRef` les enregistrements que vous créez en appelant [IMetaDataAssemblyEmit ::D efineassemblyref](../metadata/imetadataassemblyemit-defineassemblyref-method.md). .  
  
- `TypeRef` les enregistrements, que vous créez en appelant la méthode [IMetaDataEmit ::D efinetyperefbyname](../metadata/imetadataemit-definetyperefbyname-method.md) .  
  
- `TypeSpec` les enregistrements que vous créez en appelant la méthode [IMetaDataEmit :: GetTokenFromTypeSpec,](../metadata/imetadataemit-gettokenfromtypespec-method.md) .  
  
- `MemberRef` les enregistrements, que vous créez en appelant la méthode [IMetaDataEmit ::D efinememberref](../metadata/imetadataemit-definememberref-method.md) .  
  
- `MemberSpec` les enregistrements, que vous créez en appelant la méthode [IMetaDataEmit2 ::D efinemethodspec](../metadata/imetadataemit2-definemethodspec-method.md) .  
  
- `UserString` les enregistrements, que vous créez en appelant la méthode [IMetaDataEmit ::D efineuserstring](../metadata/imetadataemit-defineuserstring-method.md) .  

À compter de .NET Core 3,0, `ApplyMetaData` prend également en charge les types suivants :

- `TypeDef` les enregistrements, que vous créez en appelant la méthode [IMetaDataEmit ::D efinetypedef](../metadata/imetadataemit-definetypedef-method.md) .

- `MethodDef` les enregistrements, que vous créez en appelant la méthode [IMetaDataEmit ::D efinemethod](../metadata/imetadataemit-definemethod-method.md) . Toutefois, l’ajout de méthodes virtuelles à un type existant n’est pas pris en charge. Les méthodes virtuelles doivent être ajoutées avant le rappel de [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) .

## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo7, interface](icorprofilerinfo7-interface.md)
