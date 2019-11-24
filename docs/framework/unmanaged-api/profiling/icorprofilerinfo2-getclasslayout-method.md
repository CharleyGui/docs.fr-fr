---
title: ICorProfilerInfo2::GetClassLayout, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
ms.openlocfilehash: 37400e3b69b3884e31479fd7cdfccb473408bfbf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433393"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>ICorProfilerInfo2::GetClassLayout, méthode
Obtient des informations sur la disposition, dans la mémoire, des champs définis par la classe spécifiée. Autrement dit, cette méthode obtient les offsets des champs de la classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a>Paramètres  
 `classID`  
 [in] ID de la classe pour laquelle les informations sont récupérées.  
  
 `rFieldOffset`  
 [in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.  
  
 `cFieldOffset`  
 [in] Taille du tableau `rFieldOffset`.  
  
 `pcFieldOffset`  
 [out] Pointeur vers le nombre total d'éléments disponibles. Si `cFieldOffset` est égal à 0, cette valeur indique le nombre d'éléments requis.  
  
 `pulClassSize`  
 [out] Pointeur vers un emplacement qui contient la taille, en octets, de la classe.  
  
## <a name="remarks"></a>Notes  
 La méthode `GetClassLayout` retourne uniquement les champs définis par la classe elle-même. Si la classe parente de la classe a également défini des champs, le profileur doit appeler `GetClassLayout` sur la classe parente pour obtenir ces champs.  
  
 Si vous utilisez `GetClassLayout` avec des classes string, la méthode échoue avec le code d'erreur E_INVALIDARG. Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string. La méthode `GetClassLayout` échoue également quand elle est appelée avec une classe array.  
  
 Suite au retour de `GetClassLayout`, vous devez vérifier que la mémoire tampon `rFieldOffset` est suffisamment grande pour contenir toutes les structures `COR_FIELD_OFFSET` disponibles. Pour ce faire, comparez la valeur vers laquelle pointe `pcFieldOffset` au résultat de la division de la taille de `rFieldOffset` par la taille d'une structure `COR_FIELD_OFFSET`. Si la taille de `rFieldOffset` n'est pas suffisante, allouez une mémoire tampon `rFieldOffset` plus grande, mettez à jour `cFieldOffset` pour refléter la nouvelle taille et rappelez `GetClassLayout`.  
  
 Vous pouvez également commencer par appeler `GetClassLayout` avec un tampon `rFieldOffset` de longueur nulle pour obtenir la taille correcte du tampon. Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcFieldOffset` et rappeler `GetClassLayout`.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
