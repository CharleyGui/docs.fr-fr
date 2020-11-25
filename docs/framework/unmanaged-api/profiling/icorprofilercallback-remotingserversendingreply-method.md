---
title: ICorProfilerCallback::RemotingServerSendingReply, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerSendingReply
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerSendingReply
helpviewer_keywords:
- RemotingServerSendingReply method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerSendingReply method [.NET Framework profiling]
ms.assetid: dfe84a19-2e03-4be2-8b25-f02bad38e4a9
topic_type:
- apiref
ms.openlocfilehash: 1d876644ae35d13a481b01d9e0e5ff0d0764ca18
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713949"
---
# <a name="icorprofilercallbackremotingserversendingreply-method"></a>ICorProfilerCallback::RemotingServerSendingReply, méthode

Indique au profileur que le processus a terminé le traitement d’une demande d’appel de méthode distante et qu’il est sur le paragraphe de transmettre la réponse via un canal.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemotingServerSendingReply(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pCookie`  
 dans Pointeur vers un GUID qui correspond à la valeur fournie dans [ICorProfilerCallback :: RemotingClientReceivingReply](icorprofilercallback-remotingclientreceivingreply-method.md) dans les conditions suivantes :  
  
- Les cookies du GUID de communication à distance sont actifs.  
  
- Le canal parvient à transmettre le message.  
  
- Les cookies GUID sont actifs sur le processus côté client.  
  
 Cela permet d’associer facilement les appels de communication à distance et la création d’une pile des appels logiques.  
  
 `fIsAsync`  
 dans Valeur qui est `true` si l’appel est asynchrone ; sinon, `false` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorProfilerCallback, interface](icorprofilercallback-interface.md)
