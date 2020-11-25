---
title: ICorProfilerInfo2::GetArrayObjectInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
ms.openlocfilehash: a1e321e141059ccf1da7292d28e7099418a5134e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727196"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>ICorProfilerInfo2::GetArrayObjectInfo, méthode

Obtient des informations détaillées sur un objet de tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a>Paramètres  

 `objectId`  
 dans ID d’un objet de tableau valide.  
  
 `cDimensions`  
 dans Rang (nombre de dimensions) du tableau.  
  
 `pDimensionSizes`  
 à Tableau qui contient des entiers, chacun représentant la taille d’une dimension du tableau.  
  
 `pDimensionLowerBounds`  
 à Tableau qui contient des entiers, chacun représentant la limite inférieure d’une dimension du tableau.  
  
 `ppData`  
 à Pointeur vers l’adresse de la mémoire tampon brute pour le tableau, qui est disposé selon la Convention C++.  
  
## <a name="remarks"></a>Remarques  

 Les `pDimensionSizes` et `pDimensionLowerBounds` sont des tableaux parallèles, donc les éléments situés au même index dans chaque tableau sont des caractéristiques de la même entité.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
