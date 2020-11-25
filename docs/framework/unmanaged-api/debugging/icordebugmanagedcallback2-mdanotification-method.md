---
title: ICorDebugManagedCallback2::MDANotification, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
ms.openlocfilehash: 09a410f54ddf07c9a5f6bb7dd34f2aaf266e0734
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704576"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification, méthode

Fournit une notification indiquant que l’exécution du code a rencontré un Assistant Débogage managé (MDA) dans l’application en cours de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pController`  
 dans Pointeur vers une interface ICorDebugController qui expose le processus ou le domaine d’application dans lequel l’Assistant Débogage managé s’est produit.  
  
 Un débogueur ne doit pas faire d’hypothèses indiquant si le contrôleur est un processus ou un domaine d’application, bien qu’il puisse toujours interroger l’interface pour effectuer une détermination.  
  
 `pThread`  
 dans Pointeur vers une interface ICorDebugThread qui expose le thread managé sur lequel l’événement de débogage s’est produit.  
  
 Si l’Assistant Débogage managé s’est produit sur un thread non managé, la valeur de `pThread` est null.  
  
 Vous devez récupérer l’ID de thread du système d’exploitation à partir de l’objet MDA lui-même.  
  
 `pMDA`  
 dans Pointeur vers une interface [ICorDebugMDA](icordebugmda-interface.md) qui expose les informations de l’Assistant Débogage managé.  
  
## <a name="remarks"></a>Remarques  

 Un Assistant Débogage managé est un avertissement heuristique et ne nécessite aucune action explicite du débogueur, à l’exception de l’appel de [ICorDebugController :: continue](icordebugcontroller-continue-method.md) pour reprendre l’exécution de l’application en cours de débogage.  
  
 Le common language runtime (CLR) peut déterminer les MDA déclenchés et les données qui se trouvent dans un MDA donné à tout moment. Par conséquent, les débogueurs ne doivent pas générer de fonctionnalités nécessitant des modèles d’Assistant Débogage managé spécifiques.  
  
 Les MDA peuvent être mis en file d’attente et déclenchés peu après que l’Assistant Débogage managé a été rencontré. Cela peut se produire si le runtime doit attendre qu’il atteigne un point de sécurité pour déclencher l’Assistant Débogage managé, au lieu de déclencher l’Assistant Débogage managé lorsqu’il le rencontre. Cela signifie également que le runtime peut déclencher plusieurs MDA dans un ensemble unique de rappels mis en file d’attente (semblable à une opération d’événement d’attachement).  
  
 Un débogueur doit libérer la référence à une `ICorDebugMDA` instance immédiatement après avoir retourné le `MDANotification` rappel, pour permettre au CLR de recycler la mémoire consommée par un MDA. La libération de l’instance peut améliorer les performances si de nombreux MDA sont déclenchés.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Diagnostic d'erreurs avec les Assistants de débogage managés](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2, interface](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)
