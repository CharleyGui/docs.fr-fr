---
title: ICorProfilerInfo2::DoStackSnapshot, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 102349461456f971a2fdeaf2783630c1b88dbd6b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778630"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot, méthode
Parcourt les frames managés sur la pile pour le thread spécifié et envoie des informations au profileur via un rappel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a>Paramètres  
 `thread`  
 [in] L’ID du thread cible.  
  
 Le passage de null dans `thread` produit un instantané du thread actuel. Si un `ThreadID` d’un thread différent est passé, le common language runtime (CLR) suspend ce thread, exécute l’instantané et reprend.  
  
 `callback`  
 [in] Un pointeur vers l’implémentation de la [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) (méthode), qui est appelée par le CLR pour fournir le profileur des informations sur chaque frame managé et chaque exécution de trames non gérées.  
  
 Le `StackSnapshotCallback` méthode est implémentée par le writer de profileur.  
  
 `infoFlags`  
 [in] Une valeur de la [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) énumération qui spécifie la quantité de données à renvoyer pour chaque frame par `StackSnapshotCallback`.  
  
 `clientData`  
 [in] Un pointeur vers les données du client, qui sont transmis directement vers le `StackSnapshotCallback` fonction de rappel.  
  
 `context`  
 [in] Un pointeur vers un Win32 `CONTEXT` structure, qui est utilisé pour amorcer le parcours de pile. Win32 `CONTEXT` structure contient les valeurs des registres du processeur et représente l’état de l’UC à un moment donné dans le temps.  
  
 La valeur de départ aide le CLR à déterminer où commencer le parcours de pile, si le haut de la pile est un code non managé d’assistance ; Sinon, la valeur de départ est ignorée. Une valeur de départ doit être fournie pour un parcours asynchrone. Si vous effectuez un parcours synchrone, aucune valeur de départ n’est nécessaire.  
  
 Le `context` paramètre est valide uniquement si l’indicateur COR_PRF_SNAPSHOT_CONTEXT a été passé dans le `infoFlags` paramètre.  
  
 `contextSize`  
 [in] La taille de la `CONTEXT` structure, ce qui est référencé par le `context` paramètre.  
  
## <a name="remarks"></a>Notes  
 Le passage de null pour `thread` produit un instantané du thread actuel. Captures instantanées peuvent provenir d’autres threads uniquement si le thread cible est suspendu en temps.  
  
 Lorsque le profileur souhaite remonter la pile, il appelle `DoStackSnapshot`. Avant que le CLR est retournée à partir de cet appel, il appelle votre `StackSnapshotCallback` plusieurs fois, une fois pour chaque frame managé (ou exécution de trames non gérées) sur la pile. Lorsque des trames non gérées sont rencontrées, vous devez vous-même les parcourir.  
  
 L’ordre dans lequel la pile est parcourue est l’inverse de la façon dont les images ont été envoyées à la pile : feuille de dernière (envoyée en dernière) tout d’abord, principal (premier push) image.  
  
 Pour plus d’informations sur comment programmer le profileur permettant de remonter les piles gérées, consultez [Profiler parcours de la pile dans le .NET Framework 2.0 : Principes de base et d’autres fonctionnalités](https://go.microsoft.com/fwlink/?LinkId=73638).  
  
 Un parcours de pile peut être synchrone ou asynchrone, comme expliqué dans les sections suivantes.  
  
## <a name="synchronous-stack-walk"></a>Parcours de pile synchrone  
 Un parcours de pile synchrone implique le parcours de la pile du thread actuel en réponse à un rappel. Il ne nécessite pas l’amorçage ou à suspendre.  
  
 Vous apportez synchrone lorsque, appeler en réponse à l’appel d’un de votre profileur CLR [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (ou [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) méthodes, vous appelez `DoStackSnapshot` pour remonter la pile de la thread actuel. Cela est utile lorsque vous souhaitez voir à quoi la pile ressemble à une notification comme [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md). Vous appelez simplement `DoStackSnapshot` depuis votre `ICorProfilerCallback` méthode, en passant la valeur null dans le `context` et `thread` paramètres.  
  
## <a name="asynchronous-stack-walk"></a>Parcours de pile asynchrone  
 Un parcours de pile asynchrone implique de remonter la pile d’un thread différent, ou remonter la pile du thread actuel, pas en réponse à un rappel, mais par piratage du pointeur d’instruction du thread actif. Un parcours asynchrone requiert une valeur initiale si le haut de la pile est un code non managé qui ne fait pas partie d’une plateforme appel (PInvoke) ou appel COM, mais code d’assistance dans le CLR lui-même. Par exemple, un code qui effectue juste-à-temps (JIT) compilation ou le garbage collection est code d’assistance.  
  
 Vous obtenez une valeur initiale par directement suspende le thread cible et remonter sa pile vous-même, jusqu'à ce que vous trouviez le premier frame managé. Une fois que le thread cible est suspendu, obtenez le contexte de Registre actuel du thread cible. Ensuite, déterminez si le contexte de Registre pointe au code non managé en appelant [ICorProfilerInfo::GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) — si elle retourne un `FunctionID` égale à zéro, le frame est de code non managé. À présent, remonter la pile jusqu'à ce que la première trame gérée, puis calculer le contexte de base selon le contexte de Registre pour ce frame.  
  
 Appelez `DoStackSnapshot` avec votre contexte de base pour commencer le parcours de pile asynchrone. Si vous ne fournissez pas une valeur de départ, `DoStackSnapshot` peut ignorer les frames managés en haut de la pile et, par conséquent, vous donnera un parcours de pile incomplète. Si vous ne fournissez pas une valeur de départ, il doit pointer vers la compilation JIT ou Native Image Generator (Ngen.exe)-généré le code ; Sinon, `DoStackSnapshot` renvoie le code d’échec CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.  
  
 Parcours de pile asynchrones peuvent facilement provoquer des interblocages ou violations d’accès, sauf si vous suivez ces instructions :  
  
- Lorsque vous interrompez directement des threads, n’oubliez pas que seul un thread qui n’a jamais exécuté du code managé peut suspendre un autre thread.  
  
- Toujours bloquer votre [ICorProfilerCallback::ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) rappel jusqu'à la fin de parcours de pile de ce thread.  
  
- Ne détenez pas un verrou pendant que votre profileur appelle une fonction CLR pouvant déclencher un garbage collection. Autrement dit, ne détenez pas un verrou si le thread propriétaire peut effectuer un appel qui déclenche un garbage collection.  
  
 Il existe également un risque d’interblocage si vous appelez `DoStackSnapshot` à partir d’un thread que votre profileur a créé afin que vous pouvez parcourir la pile d’un thread cible séparé. La première fois que le thread que vous avez créé entre certaines `ICorProfilerInfo*` méthodes (y compris `DoStackSnapshot`), le CLR effectuera une initialisation par thread, spécifique au CLR sur ce thread. Si votre profileur a suspendu le thread cible dont vous essayez de parcourir la pile, et si ce thread cible est arrivé à possède un verrou nécessaires pour effectuer cette initialisation par thread, un interblocage se produit. Pour éviter ce blocage, faites un appel initial à `DoStackSnapshot` à partir de votre thread créé le profileur permettant de remonter thread cible distinct, mais n’interrompez pas le thread cible au préalable. Cet appel initial garantit que l’initialisation par thread peut s’effectuer sans blocage. Si `DoStackSnapshot` réussit et signale au moins une frame, après ce point, il sera sécurisé pour ce thread créé le profileur à interrompre n’importe quel thread cible et l’appel `DoStackSnapshot` pour remonter la pile du thread cible.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
