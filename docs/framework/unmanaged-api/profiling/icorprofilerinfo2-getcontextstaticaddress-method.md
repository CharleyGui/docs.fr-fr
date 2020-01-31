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
ms.openlocfilehash: d99e5000cdd0d7252764554025815dbace2289f4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868679"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a>ICorProfilerInfo2::GetContextStaticAddress, méthode
Obtient l’adresse du champ statique de contexte spécifié qui est dans la portée du contexte spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Parameters  
 `classId`  
 dans ID de la classe qui contient le champ statique de contexte demandé.  
  
 `fieldToken`  
 dans Jeton de métadonnées pour le champ statique de contexte demandé.  
  
 `contextId`  
 dans ID du contexte qui est la portée pour le champ statique de contexte demandé.  
  
 `ppAddress`  
 à Pointeur vers l’adresse du champ statique qui est dans le contexte spécifié.  
  
## <a name="remarks"></a>Notes  
 La méthode `GetContextStaticAddress` peut retourner l’un des éléments suivants :  
  
- CORPROF_E_DATAINCOMPLETE HRESULT si aucune adresse n’a été assignée au champ statique donné dans le contexte spécifié.  
  
- Adresses des objets qui peuvent figurer dans le tas garbage collection. Ces adresses peuvent devenir non valides après garbage collection. par conséquent, après garbage collection, les profileurs ne doivent pas supposer qu’ils sont valides.  
  
 Avant la fin du constructeur de classe d’une classe, `GetContextStaticAddress` retourne CORPROF_E_DATAINCOMPLETE pour tous ses champs statiques, bien que certains champs statiques soient déjà initialisés et que les objets de racine garbage collection.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
