---
title: IGCThreadControl::ThreadIsBlockingForSuspension, méthode
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: b5f6d7d40274972438a01313bc6aaec475b8e0c6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805088"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a>IGCThreadControl::ThreadIsBlockingForSuspension, méthode
Avertit l’hôte que le thread qui effectue l’appel est sur le présent bloqué, peut-être pour une garbage collection ou une autre suspension.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a>Notes  
 L’hôte peut choisir dans le `ThreadIsBlockingForSuspension` rappel s’il faut replanifier un thread.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IGCThreadControl, interface](igcthreadcontrol-interface.md)
