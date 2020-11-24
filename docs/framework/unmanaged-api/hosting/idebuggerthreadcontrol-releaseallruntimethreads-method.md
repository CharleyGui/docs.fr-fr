---
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads, méthode
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
ms.openlocfilehash: 490648ab8883b1dba257b82c0d0fa3c8e4783814
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684159"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a>IDebuggerThreadControl::ReleaseAllRuntimeThreads, méthode

Avertit l’hôte que les services de débogage sont sur le paragraphe de libérer tous les threads qui sont bloqués.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a>Notes  

 La `ReleaseAllRuntimeThreads` méthode ne sera jamais appelée sur un thread d’exécution. Si un thread d’exécution est bloqué sur l’hôte, il doit le libérer maintenant.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IDebuggerThreadControl, interface](idebuggerthreadcontrol-interface.md)
