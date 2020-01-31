---
title: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
ms.openlocfilehash: 945cf84e6f6201879514e29a21f7f5462aa33fdb
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868653"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs, méthode
Obtient la `FunctionID` d’une fonction à l’aide du jeton de métadonnées spécifié, de la classe conteneur et de `ClassID` valeurs de tous les arguments de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a>Parameters  
 `moduleID`  
 dans ID du module dans lequel la fonction réside.  
  
 `funcDef`  
 dans `mdMethodDef` jeton de métadonnées qui fait référence à la fonction.  
  
 `classId`  
 dans ID de la classe conteneur de la fonction.  
  
 `cTypeArgs`  
 dans Nombre de paramètres de type pour la fonction donnée. Cette valeur doit être égale à zéro pour les fonctions non génériques.  
  
 `typeArgs`  
 dans Tableau de valeurs `ClassID`, chacune d’elles étant un argument de la fonction. La valeur de `typeArgs` peut être NULL si `cTypeArgs` a la valeur zéro.  
  
 `pFunctionID`  
 à Pointeur vers l' `FunctionID` de la fonction spécifiée.  
  
## <a name="remarks"></a>Notes  
 L’appel de la méthode `GetFunctionFromTokenAndTypeArgs` avec un `mdMethodRef` des métadonnées au lieu d’un jeton de métadonnées `mdMethodDef` peut avoir des résultats imprévisibles. Les appelants doivent résoudre les `mdMethodRef` en `mdMethodDef` lors de leur passage.  
  
 Si la fonction n’est pas déjà chargée, l’appel de `GetFunctionFromTokenAndTypeArgs` entraîne le chargement, ce qui est une opération dangereuse dans de nombreux contextes. Par exemple, l’appel de cette méthode pendant le chargement de modules ou de types peut entraîner une boucle infinie, car le runtime tente de charger circulairement des éléments.  
  
 En général, l’utilisation de `GetFunctionFromTokenAndTypeArgs` est déconseillée. Si les profileurs sont intéressés par les événements pour une fonction particulière, ils doivent stocker les `ModuleID` et les `mdMethodDef` de cette fonction, et utiliser [ICorProfilerInfo2 :: GetFunctionInfo2,](icorprofilerinfo2-getfunctioninfo2-method.md) pour vérifier si une `FunctionID` donnée est celle de la fonction souhaitée.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
