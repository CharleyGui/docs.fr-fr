---
title: ICorProfilerInfo::IsArrayClass, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: 2a3f5bb0c54935e524cc955a5e11aac75b0c0923
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497554"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass, méthode
Détermine si la classe spécifiée est une classe de tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a>Paramètres  
 `classId`  
 dans ID de la classe à examiner.  
  
 `pBaseElemType`  
 à Pointeur vers une valeur de l’énumération CorElementType qui indique le type des éléments du tableau.  
  
 `pBaseClassId`  
 à Pointeur vers l’ID de classe des éléments de tableau, le cas échéant.  
  
 `pcRank`  
 à Pointeur vers un entier qui indique le rang (autrement dit, le nombre de dimensions) du tableau.  
  
## <a name="remarks"></a>Remarques  
 Si la classe spécifiée est une classe de tableau, la `IsArrayClass` méthode retourne un S_OK HRESULT et des valeurs pour tous les paramètres de sortie non null. Sinon, elle retourne S_FALSE.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
