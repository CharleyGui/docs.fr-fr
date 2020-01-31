---
title: ICorDebugStepper, interface
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
ms.openlocfilehash: e9bb69567a247472af42efb08b609d3474c87ed2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791790"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper, interface
Représente dans l'exécution du code une étape qui est effectuée par un débogueur, et qui sert d'identificateur entre l'émission et l'achèvement d'une commande tout en offrant un moyen d'annuler une étape.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Deactivate, méthode](icordebugstepper-deactivate-method.md)|Provoque l’annulation par ce `ICorDebugStepper` de la dernière commande d’étape qu’il a reçue.|  
|[IsActive, méthode](icordebugstepper-isactive-method.md)|Obtient une valeur qui indique si ce `ICorDebugStepper` exécute actuellement une étape.|  
|[SetInterceptMask, méthode](icordebugstepper-setinterceptmask-method.md)|Définit une valeur CorDebugIntercept, qui spécifie les types de code qui sont en escalier.|  
|[SetRangeIL, méthode](icordebugstepper-setrangeil-method.md)|Définit une valeur qui indique si les appels à [ICorDebugStepper :: StepRange](icordebugstepper-steprange-method.md) passent des valeurs d’argument relatives au code natif ou au code MSIL (Microsoft Intermediate Language) de la méthode qui fait l’objet d’un pas à pas.|  
|[SetUnmappedStopMask, méthode](icordebugstepper-setunmappedstopmask-method.md)|Définit une valeur CorDebugUnmappedStop, qui spécifie le type de code non mappé dans lequel l’exécution s’arrêtera.|  
|[Step, méthode](icordebugstepper-step-method.md)|Provoque `ICorDebugStepper` l’exécution d’un pas à pas détaillé dans le thread qui le contient et, éventuellement, à la poursuite d’un pas à pas détaillé dans les fonctions appelées dans le thread.|  
|[StepOut, méthode](icordebugstepper-stepout-method.md)|`ICorDebugStepper` provoque l’exécution d’une étape unique dans le thread conteneur et se termine lorsque le frame actuel retourne le contrôle au frame appelant.|  
|[StepRange, méthode](icordebugstepper-steprange-method.md)|Fait en sorte que ce `ICorDebugStepper` effectue un pas à pas détaillé dans son thread conteneur et retourne lorsqu’il atteint le code au-delà de la dernière des plages spécifiées.|  
  
## <a name="remarks"></a>Notes  
 L’interface `ICorDebugStepper` remplit les fonctions suivantes :  
  
- Il agit comme un identificateur entre une commande d’étape qui est émise et l’achèvement de cette commande.  
  
- Il fournit une interface centrale pour encapsuler toutes les exécutions pas à pas qui peuvent être effectuées.  
  
- Il offre un moyen d’annuler prématurément une opération pas à pas.  
  
 Il peut y avoir plusieurs exécutions pas à pas par thread. Par exemple, un point d’arrêt peut être atteint pendant le pas à pas principal d’une fonction, et l’utilisateur peut souhaiter démarrer une nouvelle opération pas à pas dans cette fonction. Il revient au débogueur de déterminer comment gérer cette situation. Le débogueur peut vouloir annuler l’opération pas à pas d’origine ou imbriquer les deux opérations. L’interface `ICorDebugStepper` prend en charge les deux options.  
  
 Une exécution pas à pas peut migrer entre les threads si le common language runtime (CLR) effectue un appel marshalé entre les threads.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
