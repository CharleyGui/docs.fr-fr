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
ms.openlocfilehash: 62aad8339b34a4831211a45bd645906d73393d25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727144"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs, méthode

Obtient le `ClassID` d’un type à l’aide du jeton de métadonnées spécifié et `ClassID` des valeurs de tous les arguments de type.  
  
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
 dans `mdTypeDef` Jeton de métadonnées qui référence le type.  
  
 `cTypeArgs`  
 dans Nombre de paramètres de type pour le type donné. Cette valeur doit être égale à zéro pour les types non génériques.  
  
 `typeArgs`  
 dans Tableau de `ClassID` valeurs, chacune d’entre elles étant un argument du type. La valeur de `typeArgs` peut être null si `cTypeArgs` a la valeur zéro.  
  
 `pClassID`  
 à Pointeur vers le `ClassID` du type spécifié.  
  
## <a name="remarks"></a>Remarques  

 L’appel `GetClassFromTokenAndTypeArgs` de la méthode avec un `mdTypeRef` au lieu d’un `mdTypeDef` jeton de métadonnées peut avoir des résultats imprévisibles ; les appelants doivent résoudre le `mdTypeRef` en un `mdTypeDef` lors de son passage.  
  
 Si le type n’est pas déjà chargé, l’appel de `GetClassFromTokenAndTypeArgs` déclenche le chargement, qui est une opération dangereuse dans de nombreux contextes. Par exemple, l’appel de cette méthode pendant le chargement de modules ou d’autres types peut entraîner une boucle infinie, car le runtime tente de charger circulairement des éléments.  
  
 En général, l’utilisation de `GetClassFromTokenAndTypeArgs` est déconseillée. Si les profileurs sont intéressés par les événements d’un type particulier, ils doivent stocker les `ModuleID` et `mdTypeDef` de ce type, et utiliser [ICorProfilerInfo2 :: GetClassIDInfo2,](icorprofilerinfo2-getclassidinfo2-method.md) pour vérifier si un donné `ClassID` est celui du type souhaité.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
