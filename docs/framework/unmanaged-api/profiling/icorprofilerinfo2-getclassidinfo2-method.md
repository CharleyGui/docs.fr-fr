---
title: ICorProfilerInfo2::GetClassIDInfo2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
ms.openlocfilehash: 8ce02b8b44074bed2da9e302f95a67a528601bf8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433438"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2, méthode
Obtient le module parent et le jeton de métadonnées pour la définition générique ouverte de la classe spécifiée, la `ClassID` de sa classe parente et le `ClassID` pour chaque argument de type, le cas échéant, de la classe.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `classId`  
 [in] ID de la classe pour laquelle les informations seront récupérées.  
  
 `pModuleId`  
 à Pointeur vers l’ID du module parent pour la définition générique ouverte de la classe spécifiée.  
  
 `pTypeDefToken`  
 à Pointeur vers le jeton de métadonnées pour la définition générique ouverte de la classe spécifiée.  
  
 `pParentClassId`  
 [out] Pointeur vers l'ID de la classe parente.  
  
 `cNumTypeArgs`  
 [in] Taille du tableau `typeArgs`.  
  
 `pcNumTypeArgs`  
 [out] Pointeur vers le nombre total d'éléments disponibles.  
  
 `typeArgs`  
 [out] Tableau de valeurs `ClassID`, chacune représentant l’ID d’un argument de type de la classe. Quand la méthode retourne son résultat, `typeArgs` contient une partie ou la totalité des valeurs `ClassID` disponibles.  
  
## <a name="remarks"></a>Notes  
 La méthode `GetClassIDInfo2` est semblable à la méthode [ICorProfilerInfo :: GetClassIDInfo,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) , mais `GetClassIDInfo2` obtient des informations supplémentaires sur un type générique.  
  
 Le code du profileur peut appeler [ICorProfilerInfo :: GetModuleMetaData,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) pour obtenir une interface de [métadonnées](../../../../docs/framework/unmanaged-api/metadata/index.md) pour un module donné. Le jeton de métadonnées qui est retourné à l'emplacement référencé par `pTypeDefToken` peut alors servir à accéder aux métadonnées pour la classe.  
  
 Suite au retour de `GetClassIDInfo2`, vous devez vérifier que le tampon `typeArgs` est suffisamment grand pour contenir toutes les valeurs `ClassID`. Pour ce faire, comparez la valeur vers laquelle `pcNumTypeArgs` pointe à celle du paramètre `cNumTypeArgs`. Si `pcNumTypeArgs` pointe vers une valeur supérieure à `cNumTypeArgs`, allouez une mémoire tampon `typeArgs` plus grande, mettez à jour `cNumTypeArgs` pour refléter la nouvelle taille et rappelez `GetClassIDInfo2`.  
  
 Vous pouvez également commencer par appeler `GetClassIDInfo2` avec un tampon `typeArgs` de longueur nulle pour obtenir la taille correcte du tampon. Vous pouvez ensuite définir la taille du tampon `typeArgs` sur la valeur retournée dans `pcNumTypeArgs`, puis appeler `GetClassIDInfo2` à nouveau.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
