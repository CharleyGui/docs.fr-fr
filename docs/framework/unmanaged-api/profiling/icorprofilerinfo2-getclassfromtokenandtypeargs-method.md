---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
ms.openlocfilehash: 5b6c0159b432d2a70f583357bbcf714b27399633
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447171"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs, méthode
Obtient le `ClassID` d’un type à l’aide du jeton de métadonnées spécifié et des valeurs de `ClassID` de tous les arguments de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a>Paramètres  
 `moduleID`  
 dans ID du module dans lequel le type réside.  
  
 `typeDef`  
 dans `mdTypeDef` jeton de métadonnées qui référence le type.  
  
 `cTypeArgs`  
 dans Nombre de paramètres de type pour le type donné. Cette valeur doit être égale à zéro pour les types non génériques.  
  
 `typeArgs`  
 dans Tableau de valeurs `ClassID`, chacune d’entre elles étant un argument du type. La valeur de `typeArgs` peut être NULL si `cTypeArgs` a la valeur zéro.  
  
 `pClassID`  
 à Pointeur vers le `ClassID` du type spécifié.  
  
## <a name="remarks"></a>Notes  
 L’appel de la méthode `GetClassFromTokenAndTypeArgs` avec un `mdTypeRef` au lieu d’un jeton de métadonnées `mdTypeDef` peut avoir des résultats imprévisibles ; les appelants doivent résoudre les `mdTypeRef` en `mdTypeDef` lors de leur passage.  
  
 Si le type n’est pas déjà chargé, l’appel de `GetClassFromTokenAndTypeArgs` déclenchera le chargement, ce qui constitue une opération dangereuse dans de nombreux contextes. Par exemple, l’appel de cette méthode pendant le chargement de modules ou d’autres types peut entraîner une boucle infinie, car le runtime tente de charger circulairement des éléments.  
  
 En général, l’utilisation de `GetClassFromTokenAndTypeArgs` est déconseillée. Si les profileurs sont intéressés par les événements d’un type particulier, ils doivent stocker les `ModuleID` et `mdTypeDef` de ce type, et utiliser [ICorProfilerInfo2 :: GetClassIDInfo2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) pour vérifier si un `ClassID` donné correspond à celui du type souhaité.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
