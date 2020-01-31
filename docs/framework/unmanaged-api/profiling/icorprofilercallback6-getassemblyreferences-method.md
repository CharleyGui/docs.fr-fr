---
title: ICorProfilerCallback6::GetAssemblyReferences, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
ms.openlocfilehash: 0717ef5fdb6c0447ceeb801f239be08f8cca5988
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865049"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a>ICorProfilerCallback6::GetAssemblyReferences, méthode
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Notifie le profileur qu'un assembly en est au tout début du chargement, quand le CLR (Common Langage Runtime) effectue un parcours de fermeture de références d'assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a>Parameters  
 `wszAssemblyPath`  
 [en entrée] Le chemin d’accès et le nom de l’assembly dont les métadonnées seront modifiées.  
  
 `pAsmRefProvider`  
 dans Pointeur vers l’adresse d’une interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) qui spécifie les références d’assembly à ajouter.  
  
## <a name="return-value"></a>Valeur de retour  
 Les valeurs retournées depuis ce rappel sont ignorées.  
  
## <a name="remarks"></a>Notes  
 Ce rappel est contrôlé en définissant l’indicateur de masque d’événement [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) lors de l’appel de la méthode [ICorProfilerCallback5 :: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) . Si le profileur s’inscrit à la méthode de rappel [ICorProfilerCallback6 :: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , le runtime passe le chemin d’accès et le nom de l’assembly à charger, ainsi qu’un pointeur vers un objet d’interface [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) à cette méthode. Le profileur peut ensuite appeler la méthode [ICorProfilerAssemblyReferenceProvider :: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) avec un objet `COR_PRF_ASSEMBLY_REFERENCE_INFO` pour chaque assembly cible qu’il prévoit de référencer à partir de l’assembly spécifié dans le rappel `GetAssemblyReferences`.  
  
 Utilisez le rappel de `GetAssemblyReferences` seulement si le profileur doit modifier les métadonnées d'un assembly pour y ajouter des références d'assembly. (Notez toutefois que la modification réelle des métadonnées d’un assembly est effectuée dans la méthode de rappel de [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md).) Le profileur doit implémenter la méthode de rappel `GetAssemblyReferences` pour informer le common language runtime (CLR) que les références d’assembly seront ajoutées quand le module aura été chargé.  Ceci permet de s'assurer que les décisions de partage des assemblys prises par le CLR au cours de cette phase restent valides même si le profileur prévoit de modifier ultérieurement les références d'assembly des métadonnées.  Cela permet d'éviter certaines instances où les modifications des métadonnées du profileur provoquent une erreur `SECURITY_E_INCOMPATIBLE_SHARE`.  
  
 Le profileur utilise l’objet [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) fourni par cette méthode pour ajouter des références d’assembly à l’Explorateur de fermetures de référence d’assembly CLR.  L’objet [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) doit être utilisé uniquement à partir de ce rappel. Les appels à la méthode [ICorProfilerAssemblyReferenceProvider :: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) à partir de ce rappel n’entraînent pas de métadonnées modifiées, mais uniquement dans un parcours de fermeture de référence d’assembly modifié. Le profileur doit toujours utiliser un objet [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) pour ajouter explicitement des références d’assembly à partir du rappel [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) pour l’assembly de référence, même s’il implémente le rappel `GetAssemblyReferences`.  
  
 Le profileur doit être préparé à recevoir des appels en double à ce rappel pour le même assembly et doit répondre de façon identique pour chaque appel dupliqué (en effectuant le même ensemble d’appels [ICorProfilerAssemblyReferenceProvider :: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) ).  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback6, interface](icorprofilercallback6-interface.md)
- [ModuleLoadFinished, méthode](icorprofilercallback-moduleloadfinished-method.md)
- [COR_PRF_ASSEMBLY_REFERENCE_INFO, structure](cor-prf-assembly-reference-info-structure.md)
- [ICorProfilerAssemblyReferenceProvider, interface](icorprofilerassemblyreferenceprovider-interface.md)
