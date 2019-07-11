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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e00e7f39bc2f8c14db0676102a52089c7710bd6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772255"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass, méthode
Détermine si la classe spécifiée est une classe array.  
  
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
 [in] L’ID de la classe doit être examinée.  
  
 `pBaseElemType`  
 [out] Pointeur vers une valeur de l’énumération CorElementType qui indique le type des éléments du tableau.  
  
 `pBaseClassId`  
 [out] Pointeur vers l’ID de classe des éléments du tableau, lorsqu’il est disponible.  
  
 `pcRank`  
 [out] Pointeur vers un entier qui indique le classement (autrement dit, le nombre de dimensions) du tableau.  
  
## <a name="remarks"></a>Notes  
 Si la classe spécifiée est une classe array, la `IsArrayClass` méthode retourne une valeur S_OK HRESULT et des valeurs des paramètres de sortie non null. Sinon, elle retourne S_FALSE.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
