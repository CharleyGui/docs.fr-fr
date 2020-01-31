---
title: ICorProfilerInfo2::GetStaticFieldInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
ms.openlocfilehash: d30d0bc262d76cf8980f90d8384173d89baf92d5
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862683"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a>ICorProfilerInfo2::GetStaticFieldInfo, méthode
Obtient une valeur qui indique le type de statique qui s’applique au champ spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a>Parameters  
 `classId`  
 dans ID de la classe dans laquelle le champ statique est défini.  
  
 `fieldToken`  
 dans Jeton de métadonnées pour le champ statique.  
  
 `pFieldInfo`  
 à Pointeur vers une valeur de l’énumération [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) qui indique si le champ spécifié est statique et, le cas échéant, le type de statique qui s’applique au champ.  
  
## <a name="remarks"></a>Notes  
 Ces informations peuvent être utilisées pour déterminer la fonction à appeler pour obtenir l’adresse du champ statique.  
  
 Le code du profileur doit toujours vérifier les métadonnées d’un champ statique pour s’assurer qu’il possède effectivement une adresse. Les littéraux statiques (c’est-à-dire les constantes) existent uniquement dans les métadonnées et n’ont pas d’adresse.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
