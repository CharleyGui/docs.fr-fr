---
title: ICorProfilerInfo4::RequestRevert, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
ms.openlocfilehash: c7ced05692e3030bace10dab9a6793a29fac6c26
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444841"
---
# <a name="icorprofilerinfo4requestrevert-method"></a>ICorProfilerInfo4::RequestRevert, méthode
Rétablit les versions d'origine de toutes les instances des fonctions spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a>Paramètres  
 `cFunctions`  
 [in] Nombre de fonctions à rétablir.  
  
 `moduleIds`  
 [in] Spécifie la partie `moduleId` des paires (`module`, `methodDef`) qui identifient les fonctions à rétablir.  
  
 `methodIds`  
 [in] Spécifie la partie `methodId` des paires (`module`, `methodDef`) qui identifient les fonctions à rétablir.  
  
 `status`  
 [out] Tableau de HRESULT répertoriés dans la section « HRESULT d'état » plus loin dans cette rubrique. Chaque HRESULT indique la réussite ou l'échec de la tentative de rétablissement de chaque fonction spécifiée dans les tableaux parallèles `moduleIds` et `methodIds`.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Une tentative de rétablissement de toutes les demandes a été effectuée ; toutefois, le tableau d'états retourné doit être examiné pour déterminer les fonctions qui ont été correctement rétablies.|  
|CORPROF_E_CALLBACK4_REQUIRED|The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.|  
|CORPROF_E_REJIT_NOT_ENABLED|La recompilation juste-à-temps n'a pas été activée. You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.|  
|E_INVALIDARG|`cFunctions` est égal à 0, ou `moduleIds` ou `methodIds` a la valeur `NULL`.|  
|E_OUTOFMEMORY|Le CLR n'a pas pu terminer la demande en raison d'une mémoire insuffisante.|  
  
## <a name="status-hresults"></a>HRESULT d'état  
  
|HRESULT du tableau d'états|Description|  
|--------------------------|-----------------|  
|S_OK|La fonction correspondante a été rétablie.|  
|E_INVALIDARG|Le paramètre `moduleID` ou `methodDef` est `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Le module n'est pas encore totalement chargé ou il est en cours de déchargement.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Le module spécifié a été généré dynamiquement (par exemple, par `Reflection.Emit`). Par conséquent, il n'est pas pris en charge par cette méthode.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|Le CLR ne peut pas rétablir la fonction spécifiée, car une demande de recompilation active correspondante est introuvable. La recompilation n'a jamais demandée ou la fonction a déjà été rétablie.|  
|Autre|Le système d'exploitation a retourné un échec en dehors du contrôle du CLR. Par exemple, en cas d'échec d'un appel système visant à modifier la protection d'accès d'une page de mémoire, l'erreur du système d'exploitation s'affiche.|  
  
## <a name="remarks"></a>Notes  
 Lors du prochain appel des instances de la fonction rétablie, les versions d'origine des fonctions seront exécutées. Si une fonction est déjà en cours d'exécution, il termine l'exécution de la version en cours d'exécution.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo4, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
