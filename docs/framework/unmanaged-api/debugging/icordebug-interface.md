---
title: ICorDebug, interface
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
ms.openlocfilehash: 21838bdd8ff45f8f74524dc4da52364fb032b396
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723400"
---
# <a name="icordebug-interface"></a>ICorDebug, interface

Fournit des méthodes qui permettent aux développeurs de déboguer des applications dans l’environnement du common language runtime (CLR).  
  
> [!NOTE]
> Le débogage en mode mixte (code managé et natif) n’est pas pris en charge sur Windows 95, Windows 98 ou Windows ME, ni sur les plateformes autres que x86 (telles que IA64 et AMD64).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CanLaunchOrAttach, méthode](icordebug-canlaunchorattach-method.md)|Détermine si le lancement d’un nouveau processus ou l’attachement au processus donné est possible dans le contexte de la configuration d’ordinateur et d’exécution actuelle.|  
|[CreateProcess, méthode](icordebug-createprocess-method.md)|Lance un processus et son thread principal sous le contrôle du débogueur.|  
|[DebugActiveProcess, méthode](icordebug-debugactiveprocess-method.md)|Joint le débogueur à un processus existant.|  
|[EnumerateProcesses, méthode](icordebug-enumerateprocesses-method.md)|Obtient un énumérateur pour les processus en cours de débogage.|  
|[GetProcess, méthode](icordebug-getprocess-method.md)|Retourne l’objet « ICorDebugProcess » avec l’ID de processus donné.|  
|[Initialize, méthode](icordebug-initialize-method.md)|Initialise l'objet `ICorDebug`.|  
|[SetManagedHandler, méthode](icordebug-setmanagedhandler-method.md)|Spécifie l’objet de gestionnaire d’événements pour les événements managés.|  
|[SetUnmanagedHandler, méthode](icordebug-setunmanagedhandler-method.md)|Spécifie l’objet de gestionnaire d’événements pour les événements non managés.|  
|[Terminate, méthode](icordebug-terminate-method.md)|Met fin à l' `ICorDebug` objet.|  
  
## <a name="remarks"></a>Remarques  

 `ICorDebug` représente une boucle de traitement des événements pour un processus du débogueur. Le débogueur doit attendre le rappel [ICorDebugManagedCallback :: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) de tous les processus en cours de débogage avant de libérer cette interface.  
  
 L' `ICorDebug` objet est l’objet initial pour contrôler tout le débogage managé. Dans les versions 1,0 et 1,1 de .NET Framework, cet objet était un `CoClass` objet créé à partir de com. Dans la version 2,0 de .NET Framework, cet objet n’est plus un `CoClass` objet. Elle doit être créée par la fonction [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) , qui prend en charge la version. Cette nouvelle fonction de création permet aux clients d’obtenir une implémentation spécifique de `ICorDebug` , qui émule également une version spécifique de l’API de débogage.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
