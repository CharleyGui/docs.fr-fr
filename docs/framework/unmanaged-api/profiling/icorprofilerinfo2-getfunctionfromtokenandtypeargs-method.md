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
ms.openlocfilehash: 17a6220598010c0bee9c3f0485860aa0b2dc5f3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727105"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs, méthode

Obtient le `FunctionID` d’une fonction à l’aide du jeton de métadonnées spécifié, de la classe conteneur et `ClassID` des valeurs de tous les arguments de type.  
  
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
  
## <a name="parameters"></a>Paramètres  

 `moduleID`  
 dans ID du module dans lequel la fonction réside.  
  
 `funcDef`  
 dans `mdMethodDef` Jeton de métadonnées qui fait référence à la fonction.  
  
 `classId`  
 dans ID de la classe conteneur de la fonction.  
  
 `cTypeArgs`  
 dans Nombre de paramètres de type pour la fonction donnée. Cette valeur doit être égale à zéro pour les fonctions non génériques.  
  
 `typeArgs`  
 dans Tableau de `ClassID` valeurs, dont chacune est un argument de la fonction. La valeur de `typeArgs` peut être null si `cTypeArgs` a la valeur zéro.  
  
 `pFunctionID`  
 à Pointeur vers le `FunctionID` de la fonction spécifiée.  
  
## <a name="remarks"></a>Remarques  

 L’appel `GetFunctionFromTokenAndTypeArgs` de la méthode avec des `mdMethodRef` métadonnées au lieu d’un `mdMethodDef` jeton de métadonnées peut avoir des résultats imprévisibles. Les appelants doivent résoudre le `mdMethodRef` en un `mdMethodDef` lors de leur passage.  
  
 Si la fonction n’est pas déjà chargée, l’appel de entraîne le `GetFunctionFromTokenAndTypeArgs` chargement, ce qui constitue une opération dangereuse dans de nombreux contextes. Par exemple, l’appel de cette méthode pendant le chargement de modules ou de types peut entraîner une boucle infinie, car le runtime tente de charger circulairement des éléments.  
  
 En général, l’utilisation de `GetFunctionFromTokenAndTypeArgs` est déconseillée. Si les profileurs sont intéressés par les événements pour une fonction particulière, ils doivent stocker les `ModuleID` et `mdMethodDef` de cette fonction, et utiliser [ICorProfilerInfo2 :: GetFunctionInfo2,](icorprofilerinfo2-getfunctioninfo2-method.md) pour vérifier si un donné `FunctionID` est celui de la fonction souhaitée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
