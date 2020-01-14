---
title: ICorProfilerInfo3::RequestProfilerDetach, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.RequestProfilerDetach Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type:
- apiref
ms.openlocfilehash: 226f24ad8f1636101b283c3cb6662905cbf7eebe
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938206"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach, méthode
Indique au runtime de détacher le profileur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a>Parameters  
 `dwExpectedCompletionMilliseconds`  
 [in] Durée, en millisecondes, pendant laquelle le Common Language Runtime (CLR) doit attendre avant de vérifier si le déchargement du profileur peut être exécuté en tout sécurité.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La demande de détachement est valide, et la procédure de détachement se poursuit maintenant sur un autre thread. Une fois le détachement terminé, un événement `ProfilerDetachSucceeded` est émis.|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|Le profileur a échoué une tentative [IUnknown :: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) pour l’interface [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) , qu’il doit implémenter pour prendre en charge l’opération de détachement. La tentative de détachement n'a pas eu lieu.|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|Le détachement est impossible, car le profileur a défini des indicateurs immuables au démarrage. La tentative de détachement n'a pas eu lieu ; le profileur est toujours entièrement attaché.|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|Le détachement est impossible, car le profileur a utilisé du code MSIL (Microsoft Intermediate Language) instrumenté ou inséré `enter`/des hooks `leave`. La tentative de détachement n'a pas eu lieu ; le profileur est toujours entièrement attaché.<br /><br /> **Remarque** Le code MSIL instrumenté est le code fourni par le profileur à l’aide de la méthode [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) .|  
|CORPROF_E_RUNTIME_UNINITIALIZED|Le runtime n'a pas encore été initialisé dans l'application managée. (Autrement dit, le runtime n’a pas été entièrement chargé.) Ce code d’erreur peut être retourné lorsque le détachement est demandé à l’intérieur de la méthode [ICorProfilerCallback :: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) du rappel du profileur.|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach` a été appelée à une heure non prise en charge. Cela se produit si la méthode est appelée sur un thread managé, mais pas à partir d’une méthode [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) , ou à partir d’une méthode [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) qui ne peut pas tolérer un garbage collection. Pour plus d’informations, consultez [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).|  
  
## <a name="remarks"></a>Notes  
 Pendant la procédure de détachement, le thread de détachement (thread créé spécifiquement pour détacher le profileur) vérifie parfois si tous les threads ont quitté le code du profileur. Le profileur doit fournir une estimation de la durée de cette opération via le paramètre `dwExpectedCompletionMilliseconds`. Une valeur appropriée à utiliser est le temps passé par le profileur dans une méthode `ICorProfilerCallback*` donnée ; cette valeur ne doit pas être inférieure à la moitié du temps maximal que le profileur prévoit de passer.  
  
 Le thread de détachement utilise `dwExpectedCompletionMilliseconds` pour décider de la durée de la veille avant de vérifier si le code de rappel du profileur a été dépilé. Bien que les détails de l’algorithme suivant puissent changer dans les mises en production ultérieures du CLR, il illustre comment `dwExpectedCompletionMilliseconds` peut être utilisé pour déterminer si le profileur peut être déchargé en toute sécurité. Le thread de détachement est d'abord en veille pendant `dwExpectedCompletionMilliseconds` millisecondes. Si, après avoir quitté le mode veille, le CLR détecte que le code de rappel du profileur est encore présent, le thread de détachement est de nouveau mis en veille, cette fois pour deux fois `dwExpectedCompletionMilliseconds` millisecondes. Si, après avoir quitté ce deuxième état de veille, le thread de détachement détermine que le code de rappel du profileur est encore présent, il repasse en état de veille pendant 10 minutes avant d'effectuer une nouvelle vérification. Le thread de détachement procède à une revérification toutes les 10 minutes.  
  
 Si le profileur affecte à `dwExpectedCompletionMilliseconds` la valeur 0 (zéro), le CLR utilise une valeur par défaut de 5000, ce qui signifie qu'il effectue une vérification après 5 secondes, une autre après 10 secondes, puis toutes les 10 minutes.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo3, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
