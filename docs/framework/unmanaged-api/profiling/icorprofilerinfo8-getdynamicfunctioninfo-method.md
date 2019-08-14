---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 90246ade67f797c04f0da5d9a68dadb83e4ce418
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973859"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a>ICorProfilerInfo8:: GetDynamicFunctionInfo, méthode
  
 Récupère des informations sur les méthodes dynamiques.
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```  
  
#### <a name="parameters"></a>Paramètres  
 `functionId`  
 dans ID de la fonction pour laquelle des informations doivent être récupérées.  

 `moduleId`  
 dans Pointeur vers le module dans lequel la classe parente de la fonction est définie.  
  
 `ppvSig`  
 à Pointeur vers la signature de la fonction.  
  
 `pbSig`  
 à Pointeur vers le nombre d’octets pour la signature de fonction.
  
 `cchName`  
 [in] Taille maximale du tableau `wszName`.
  
 `pcchName`  
 à Nombre de caractères dans le `wszName` tableau.

 `wszName` \
 à Tableau d `WCHAR` 'qui est le nom de la fonction, s’il en existe un.
  
## <a name="remarks"></a>Notes  
 Certaines méthodes telles que les stubs IL ou les LCG n’ont pas de métadonnées associées qui peuvent être récupérées à l’aide des API [IMetaDataImport](../metadata/imetadataimport-interface.md) et [IMetaDataImport2](../metadata/imetadataimport2-interface.md) . Ces méthodes peuvent être rencontrées par les profileurs par le biais de pointeurs d’instruction ou en écoutant [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).

 Cette API peut être utilisée pour récupérer des informations sur les méthodes dynamiques, y compris un nom convivial, si disponible.  
  

## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf. idl, CorProf. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions de .NET Framework:** [! INCLURE[net_current_v472plus](../../../../includes/net-current-v472plus.md)  
  
## <a name="see-also"></a>Voir aussi
- [Interface ICorProfilerInfo8](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

