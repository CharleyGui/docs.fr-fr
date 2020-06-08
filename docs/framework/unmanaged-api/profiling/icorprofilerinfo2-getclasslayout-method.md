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
ms.openlocfilehash: ac35b18ce8c45c95bb2fb8e820423470ca1b75bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497151"
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
 [in, out] Tableau de structures [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) , chacune contenant les jetons et les offsets des champs de la classe.  
  
 `cFieldOffset`  
 [in] Taille du tableau `rFieldOffset`.  
  
 `pcFieldOffset`  
 [out] Pointeur vers le nombre total d'éléments disponibles. Si `cFieldOffset` est égal à 0, cette valeur indique le nombre d'éléments requis.  
  
 `pulClassSize`  
 [out] Pointeur vers un emplacement qui contient la taille, en octets, de la classe.  
  
## <a name="remarks"></a>Remarques  
 La méthode `GetClassLayout` retourne uniquement les champs définis par la classe elle-même. Si la classe parente de la classe a également défini des champs, le profileur doit appeler `GetClassLayout` sur la classe parente pour obtenir ces champs.  
  
 Si vous utilisez `GetClassLayout` avec des classes string, la méthode échoue avec le code d'erreur E_INVALIDARG. Utilisez [ICorProfilerInfo2 :: GetStringLayout,](icorprofilerinfo2-getstringlayout-method.md) pour obtenir des informations sur la disposition d’une chaîne. La méthode `GetClassLayout` échoue également quand elle est appelée avec une classe array.  
  
 Suite au retour de `GetClassLayout`, vous devez vérifier que la mémoire tampon `rFieldOffset` est suffisamment grande pour contenir toutes les structures `COR_FIELD_OFFSET` disponibles. Pour ce faire, comparez la valeur vers laquelle pointe `pcFieldOffset` au résultat de la division de la taille de `rFieldOffset` par la taille d'une structure `COR_FIELD_OFFSET`. Si la taille de `rFieldOffset` n'est pas suffisante, allouez une mémoire tampon `rFieldOffset` plus grande, mettez à jour `cFieldOffset` pour refléter la nouvelle taille et rappelez `GetClassLayout`.  
  
 Vous pouvez également commencer par appeler `GetClassLayout` avec un tampon `rFieldOffset` de longueur nulle pour obtenir la taille correcte du tampon. Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcFieldOffset` et rappeler `GetClassLayout`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
