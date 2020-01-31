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
ms.openlocfilehash: 73d122b1ffa890bfa43f8eef7e24595ac0d26ebe
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861786"
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
  
## <a name="parameters"></a>Parameters  
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
|CORPROF_E_CALLBACK4_REQUIRED|Le profileur doit implémenter l’interface [ICorProfilerCallback4](icorprofilercallback4-interface.md) pour que cet appel soit pris en charge.|  
|CORPROF_E_REJIT_NOT_ENABLED|La recompilation juste-à-temps n'a pas été activée. Vous devez activer la recompilation JIT pendant l’initialisation à l’aide de la méthode [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md) pour définir l’indicateur `COR_PRF_ENABLE_REJIT`.|  
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
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo4, interface](icorprofilerinfo4-interface.md)
- [Interfaces de profilage](profiling-interfaces.md)
- [Profilage](index.md)
