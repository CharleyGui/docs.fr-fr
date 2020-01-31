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
ms.openlocfilehash: bf9ea40cc81be37499e6729006e7177a8000c000
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793296"
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
  
## <a name="parameters"></a>Parameters  
 `pController`  
 dans Pointeur vers une interface ICorDebugController qui expose le processus ou le domaine d’application dans lequel l’Assistant Débogage managé s’est produit.  
  
 Un débogueur ne doit pas faire d’hypothèses indiquant si le contrôleur est un processus ou un domaine d’application, bien qu’il puisse toujours interroger l’interface pour effectuer une détermination.  
  
 `pThread`  
 dans Pointeur vers une interface ICorDebugThread qui expose le thread managé sur lequel l’événement de débogage s’est produit.  
  
 Si l’Assistant Débogage managé s’est produit sur un thread non managé, la valeur de `pThread` sera null.  
  
 Vous devez récupérer l’ID de thread du système d’exploitation à partir de l’objet MDA lui-même.  
  
 `pMDA`  
 dans Pointeur vers une interface [ICorDebugMDA](icordebugmda-interface.md) qui expose les informations de l’Assistant Débogage managé.  
  
## <a name="remarks"></a>Notes  
 Un Assistant Débogage managé est un avertissement heuristique et ne nécessite aucune action explicite du débogueur, à l’exception de l’appel de [ICorDebugController :: continue](icordebugcontroller-continue-method.md) pour reprendre l’exécution de l’application en cours de débogage.  
  
 Le common language runtime (CLR) peut déterminer les MDA déclenchés et les données qui se trouvent dans un MDA donné à tout moment. Par conséquent, les débogueurs ne doivent pas générer de fonctionnalités nécessitant des modèles d’Assistant Débogage managé spécifiques.  
  
 Les MDA peuvent être mis en file d’attente et déclenchés peu après que l’Assistant Débogage managé a été rencontré. Cela peut se produire si le runtime doit attendre qu’il atteigne un point de sécurité pour déclencher l’Assistant Débogage managé, au lieu de déclencher l’Assistant Débogage managé lorsqu’il le rencontre. Cela signifie également que le runtime peut déclencher plusieurs MDA dans un ensemble unique de rappels mis en file d’attente (semblable à une opération d’événement d’attachement).  
  
 Un débogueur doit libérer la référence à une instance de `ICorDebugMDA` immédiatement après avoir retourné le rappel `MDANotification`, afin de permettre au CLR de recycler la mémoire consommée par un Assistant Débogage managé. La libération de l’instance peut améliorer les performances si de nombreux MDA sont déclenchés.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2, interface](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interface](icordebugmanagedcallback-interface.md)
