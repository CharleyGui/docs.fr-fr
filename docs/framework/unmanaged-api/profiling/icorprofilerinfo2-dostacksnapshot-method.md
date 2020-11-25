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
ms.openlocfilehash: 10cc9dedfa34cd5235df721d7010bbd928fbc3ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727235"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot, méthode

Parcourt les frames managés sur la pile pour le thread spécifié et envoie des informations au profileur par le biais d’un rappel.  
  
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
 dans ID du thread cible.  
  
 Le passage de NULL dans `thread` produit un instantané du thread en cours. Si un `ThreadID` d’un thread différent est passé, le Common Language Runtime (CLR) interrompt ce thread, exécute l’instantané, puis reprend.  
  
 `callback`  
 dans Pointeur vers l’implémentation de la méthode [StackSnapshotCallback](stacksnapshotcallback-function.md) , qui est appelée par le CLR pour fournir au profileur des informations sur chaque frame managé et chaque exécution de frames non managés.  
  
 La `StackSnapshotCallback` méthode est implémentée par le writer du profileur.  
  
 `infoFlags`  
 dans Valeur de l’énumération [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) , qui spécifie la quantité de données à repasser pour chaque frame par `StackSnapshotCallback` .  
  
 `clientData`  
 dans Pointeur vers les données du client, qui est passé directement à la `StackSnapshotCallback` fonction de rappel.  
  
 `context`  
 dans Pointeur vers une structure Win32 `CONTEXT` qui est utilisée pour amorcer le parcours de la pile. La `CONTEXT` structure Win32 contient des valeurs des registres de l’UC et représente l’état de l’UC à un moment précis dans le temps.  
  
 La valeur de départ aide le CLR à déterminer où commencer le parcours de la pile, si le haut de la pile est un code d’assistance non managé ; dans le cas contraire, la valeur initiale est ignorée. Une valeur de départ doit être fournie pour une procédure asynchrone. Si vous effectuez une procédure synchrone, aucune valeur de départ n’est nécessaire.  
  
 Le `context` paramètre n’est valide que si l’indicateur COR_PRF_SNAPSHOT_CONTEXT a été passé dans le `infoFlags` paramètre.  
  
 `contextSize`  
 dans Taille de la `CONTEXT` structure, qui est référencée par le `context` paramètre.  
  
## <a name="remarks"></a>Remarques  

 Le passage de la valeur null à `thread` génère un instantané du thread actuel. Les instantanés ne peuvent être utilisés par d’autres threads que si le thread cible est suspendu à ce moment-là.  
  
 Quand le profileur souhaite remonter la pile, il appelle `DoStackSnapshot` . Avant que le CLR ne retourne à partir de cet appel, il appelle `StackSnapshotCallback` plusieurs fois, une fois pour chaque frame managé (ou l’exécution de frames non managés) sur la pile. Lorsque des frames non managés sont détectés, vous devez les parcourir vous-même.  
  
 L’ordre dans lequel la pile est parcourue est l’inverse de la façon dont les frames ont fait l’objet d’un push sur la pile : Frame (dernier push) frame en premier, Frame principal (premier-push) en dernier.  
  
 Pour plus d’informations sur la façon de programmer le profileur pour parcourir les piles managées, consultez [parcours de la pile du profileur dans le .NET Framework 2,0 : notions de base et au-delà](/previous-versions/dotnet/articles/bb264782(v=msdn.10)).  
  
 Un parcours de pile peut être synchrone ou asynchrone, comme expliqué dans les sections suivantes.  
  
## <a name="synchronous-stack-walk"></a>Parcours de pile synchrone  

 Un parcours de pile synchrone implique le parcours de la pile du thread actuel en réponse à un rappel. Elle ne nécessite pas d’amorçage ou de suspension.  
  
 Vous effectuez un appel synchrone quand, en réponse au CLR appelant l’une des méthodes [ICorProfilerCallback](icorprofilercallback-interface.md) (ou [ICorProfilerCallback2](icorprofilercallback2-interface.md)) de votre profileur, vous appelez `DoStackSnapshot` pour parcourir la pile du thread actuel. Cela est utile lorsque vous souhaitez voir à quoi ressemble la pile dans une notification telle que [ICorProfilerCallback :: ObjectAllocated](icorprofilercallback-objectallocated-method.md). Vous appelez simplement `DoStackSnapshot` à partir de votre `ICorProfilerCallback` méthode, en passant la valeur null dans les `context` `thread` paramètres et.  
  
## <a name="asynchronous-stack-walk"></a>Parcours de pile asynchrone  

 Un parcours de pile asynchrone implique le parcours de la pile d’un thread différent, ou le parcours de la pile du thread actuel, et non en réponse à un rappel, mais en détournent le pointeur d’instruction du thread actuel. Un parcours asynchrone requiert une valeur de départ si le haut de la pile est du code non managé qui ne fait pas partie d’un appel de code non managé (PInvoke) ou d’un appel COM, mais code d’assistance dans le CLR lui-même. Par exemple, le code qui effectue une compilation juste-à-temps (JIT) ou garbage collection est un code d’assistance.  
  
 Vous obtenez une valeur de départ en suspendant directement le thread cible et en parcourant sa pile vous-même, jusqu’à ce que vous trouviez le frame managé le plus haut. Une fois le thread cible suspendu, obtient le contexte de registre actuel du thread cible. Ensuite, déterminez si le contexte de registre pointe vers du code non managé en appelant [ICorProfilerInfo :: GetFunctionFromIP,](icorprofilerinfo-getfunctionfromip-method.md) : s’il retourne un `FunctionID` égal à zéro, le frame est du code non managé. À présent, parcourez la pile jusqu’à ce que vous atteigniez le premier frame géré, puis calculez le contexte de départ en fonction du contexte de registre de ce frame.  
  
 Appelez `DoStackSnapshot` avec votre contexte de valeur initiale pour commencer le parcours de la pile asynchrone. Si vous ne fournissez pas de valeur de départ, `DoStackSnapshot` peut ignorer des frames managés en haut de la pile et, par conséquent, vous donnera un parcours de pile incomplet. Si vous fournissez une valeur de départ, elle doit pointer vers du code généré juste-à-temps ou un générateur d’images natives (Ngen.exe). Sinon, `DoStackSnapshot` retourne le code d’échec, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.  
  
 Les parcours de pile asynchrones peuvent facilement provoquer des interblocages ou des violations d’accès, sauf si vous suivez ces instructions :  
  
- Lorsque vous suspendez directement les threads, n’oubliez pas que seul un thread qui n’a jamais exécuté du code managé peut suspendre un autre thread.  
  
- Bloquez toujours dans votre rappel [ICorProfilerCallback :: ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md) jusqu’à ce que le parcours de la pile de ce thread soit terminé.  
  
- Ne conservez pas de verrou pendant que votre profileur appelle dans une fonction CLR qui peut déclencher un garbage collection. Autrement dit, ne pas conserver de verrou si le thread propriétaire peut effectuer un appel qui déclenche un garbage collection.  
  
 Il y a également un risque d’interblocage si vous appelez `DoStackSnapshot` à partir d’un thread que votre profileur a créé afin que vous puissiez parcourir la pile d’un thread cible séparé. La première fois que le thread que vous avez créé entre dans certaines `ICorProfilerInfo*` méthodes (y compris `DoStackSnapshot` ), le CLR effectuera une initialisation par thread et spécifique au CLR sur ce thread. Si votre profileur a suspendu le thread cible dont vous tentez de parcourir la pile, et si ce thread cible est devenu propriétaire d’un verrou nécessaire pour effectuer cette initialisation par thread, un interblocage se produit. Pour éviter ce blocage, effectuez un appel initial `DoStackSnapshot` de à partir de votre thread créé par le profileur pour parcourir un thread cible séparé, mais n’interrompez pas d’abord le thread cible. Cet appel initial garantit que l’initialisation par thread peut se terminer sans interblocage. Si `DoStackSnapshot` suit et signale au moins un frame, après ce point, il est possible pour ce thread créé par le profileur d’interrompre n’importe quel thread cible et `DoStackSnapshot` d’appeler pour parcourir la pile de ce thread cible.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerInfo, interface](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interface](icorprofilerinfo2-interface.md)
