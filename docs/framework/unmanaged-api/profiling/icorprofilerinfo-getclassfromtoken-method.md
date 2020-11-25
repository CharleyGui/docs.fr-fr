---
title: ICorProfilerInfo::GetClassFromToken, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
ms.openlocfilehash: 7d9fe7d6d5c5af32be22ba19b52e7d40033a6eb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706747"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a>ICorProfilerInfo::GetClassFromToken, méthode

Obtient l’ID de la classe, en fonction du jeton de métadonnées. Cette méthode est obsolète dans la version 2,0 de .NET Framework. Utilisez [ICorProfilerInfo2 :: GetClassFromTokenAndTypeArgs,](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a>Paramètres  

 `moduleID`  
 dans ID du module qui contient la classe.  
  
 `typeDef`  
 dans Un `mdTypeDef` jeton de métadonnées qui fait référence à la classe.  
  
 `cTypeArgs`  
 à Pointeur vers l’ID de classe.  
  
## <a name="remarks"></a>Remarques  

 Cette méthode est obsolète ; Utilisez plutôt `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` pour tous les types.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :** 1,0, 1,1  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
