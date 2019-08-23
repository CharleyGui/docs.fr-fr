---
title: ICorDebugDataTarget, interface
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c6a8ee1bcc65e640ef871e57acdeef21acd7896
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930822"
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget, interface
Fournit une interface de rappel qui permet d'accéder à un processus cible particulier.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPlatform, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|Fournit des informations sur la plateforme, y compris l’architecture du processeur et le système d’exploitation, sur lesquelles le processus cible est en cours d’exécution.|  
|[ReadVirtual, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|Obtient un bloc de mémoire contiguë commençant à l’adresse spécifiée et le retourne dans la mémoire tampon fournie.|  
|[GetThreadContext, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|Demande le contexte de thread actuel pour le thread spécifié.|  
  
## <a name="remarks"></a>Notes  
 `ICorDebugDataTarget`et ses méthodes présentent les caractéristiques suivantes:  
  
- Les services de débogage appellent des méthodes sur cette interface pour accéder à la mémoire et à d’autres données dans le processus cible.  
  
- Le client du débogueur doit implémenter cette interface de manière appropriée pour la cible particulière (par exemple, un processus en direct ou un vidage de mémoire).  
  
- Les `ICorDebugDataTarget` méthodes ne peuvent être appelées qu’à partir de méthodes implémentées dans d’autres `ICorDebug*` interfaces. Cela permet de s’assurer que le client du débogueur contrôle le thread sur lequel il est appelé, et à quel moment.  
  
- L' `ICorDebugDataTarget` implémentation doit toujours retourner des informations à jour sur la cible.  
  
 Le processus cible doit être arrêté et ne pas être modifié de quelque `ICorDebug*` manière que ce soit `ICorDebugDataTarget` pendant que les interfaces (et par conséquent les méthodes) sont appelées. Si la cible est un processus en direct et que son état change, la méthode [ICLRDebugging:: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) doit être à nouveau appelée pour fournir une instance de remplacement de ICorDebugProcess.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorDebug. h  
  
 **Bibliothèque** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
