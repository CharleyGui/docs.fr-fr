---
title: IDebuggerThreadControl, interface
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
ms.openlocfilehash: 82c6113f4df3334500128df22f7e9ce8d4bf151f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805276"
---
# <a name="idebuggerthreadcontrol-interface"></a>IDebuggerThreadControl, interface
Fournit des méthodes pour notifier l’hôte concernant le blocage et le déblocage de threads par les services de débogage.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ThreadIsBlockingForDebugger, méthode](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|Avertit l’hôte que le thread qui envoie ce rappel va être bloqué dans les services de débogage.|  
|[ReleaseAllRuntimeThreads, méthode](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|Avertit l’hôte que les services de débogage sont sur le paragraphe de libérer tous les threads qui sont bloqués.|  
|[StartBlockingForDebugger, méthode](idebuggerthreadcontrol-startblockingfordebugger-method.md)|Avertit l’hôte que les services de débogage sont sur le paragraphe duquel ils commencent à bloquer tous les threads.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces d'hébergement](hosting-interfaces.md)
