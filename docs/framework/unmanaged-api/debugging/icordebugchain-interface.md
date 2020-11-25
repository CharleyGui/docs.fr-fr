---
title: ICorDebugChain, interface
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
ms.openlocfilehash: a0285970a8a42c078aa663579e1d5998d0d1c037
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724453"
---
# <a name="icordebugchain-interface"></a>ICorDebugChain, interface

Représente un segment d'une pile des appels physique ou logique.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumerateFrames, méthode](icordebugchain-enumerateframes-method.md)|Obtient un énumérateur qui contient tous les frames de pile managés dans la chaîne, en commençant par le frame le plus récent.|  
|[GetActiveFrame, méthode](icordebugchain-getactiveframe-method.md)|Obtient le frame actif (c’est-à-dire le plus récent) de la chaîne.|  
|[GetCallee, méthode](icordebugchain-getcallee-method.md)|Obtient la chaîne qui a été appelée par cette chaîne.|  
|[GetCaller, méthode](icordebugchain-getcaller-method.md)|Obtient la chaîne qui a appelé cette chaîne.|  
|[GetContext, méthode](icordebugchain-getcontext-method.md)|Non implémenté.|  
|[GetNext, méthode](icordebugchain-getnext-method.md)|Obtient la chaîne suivante de frames pour le thread.|  
|[GetPrevious, méthode](icordebugchain-getprevious-method.md)|Obtient la chaîne précédente des frames pour le thread.|  
|[GetReason, méthode](icordebugchain-getreason-method.md)|Obtient la raison pour le Genesis de cette chaîne d’appel.|  
|[GetRegisterSet, méthode](icordebugchain-getregisterset-method.md)|Obtient le Registre défini pour la partie active de cette chaîne.|  
|[GetStackRange, méthode](icordebugchain-getstackrange-method.md)|Obtient la plage d’adresses du segment de pile pour cette chaîne.|  
|[GetThread, méthode](icordebugchain-getthread-method.md)|Obtient le thread physique dont fait partie cette chaîne d’appel.|  
|[IsManaged, méthode](icordebugchain-ismanaged-method.md)|Obtient une valeur qui indique si cette chaîne exécute du code managé.|  
  
## <a name="remarks"></a>Remarques  

 Les frames de pile dans une chaîne occupent un espace de pile contigu et partagent le même thread et le même contexte. Une chaîne peut représenter des chaînes de code managées ou non managées. Une `ICorDebugChain` instance vide représente une chaîne de code non managé.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
