---
title: ICorProfilerInfo2::GetContextStaticAddress, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c5c8165d44cc3a305820f8e97c07da37f2a0693
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775805"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a>ICorProfilerInfo2::GetContextStaticAddress, méthode
Obtient l’adresse pour le champ statique de contexte spécifié qui est dans la portée du contexte spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Paramètres  
 `classId`  
 [in] ID de la classe qui contient le champ statique de contexte demandé.  
  
 `fieldToken`  
 [in] Le jeton de métadonnées pour le champ statique de contexte demandé.  
  
 `contextId`  
 [in] ID du contexte qui est la portée pour le champ statique de contexte demandé.  
  
 `ppAddress`  
 [out] Pointeur vers l’adresse du champ statique qui est dans le contexte spécifié.  
  
## <a name="remarks"></a>Notes  
 Le `GetContextStaticAddress` méthode peut retourner l’une des opérations suivantes :  
  
- Un HRESULT CORPROF_E_DATAINCOMPLETE si le champ statique donné n’a pas été assigné une adresse dans le contexte spécifié.  
  
- Les adresses des objets qui peuvent être dans le tas de garbage collection. Ces adresses peuvent devenir non valides après le garbage collection, donc après le garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.  
  
 Avant la fin de constructeur de classe d’une classe, `GetContextStaticAddress` retournera CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains des champs statiques peuvent déjà être initialisés et utiliser des objets de garbage collection racine.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
