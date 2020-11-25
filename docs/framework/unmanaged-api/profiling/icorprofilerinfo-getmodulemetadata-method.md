---
title: ICorProfilerInfo::GetModuleMetaData, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: 74df0fb412e7fb3d9f779391ec84f07a0379a2cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724115"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData, méthode

Obtient une instance d’interface de métadonnées mappée au module spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a>Paramètres  

 `moduleId`  
 dans ID du module auquel l’instance d’interface sera mappée.  
  
 `dwOpenFlags`  
 dans Valeur de l’énumération [CorOpenFlags](../metadata/coropenflags-enumeration.md) qui spécifie le mode d’ouverture des fichiers manifeste. Seuls les `ofRead` `ofWrite` bits et `ofNoTransform` sont valides.  
  
 `riid`  
 dans ID de référence (GUID) de l’interface de métadonnées dont l’instance sera récupérée. Consultez la page [interfaces de métadonnées](../metadata/metadata-interfaces.md) pour obtenir la liste des interfaces.  
  
 `ppOut`  
 à Pointeur vers l’adresse de l’instance de l’interface de métadonnées.  
  
## <a name="remarks"></a>Remarques  

 Vous pouvez demander que les métadonnées soient ouvertes en mode lecture/écriture, mais cela entraîne une exécution plus lente des métadonnées du programme, car les modifications apportées aux métadonnées ne peuvent pas être optimisées comme elles le faisaient du compilateur.  
  
 Certains modules (tels que les modules de ressources) n’ont pas de métadonnées. Dans ce cas, `GetModuleMetaData` retourne une valeur HRESULT de S_FALSE et une valeur null dans * `ppOut` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
