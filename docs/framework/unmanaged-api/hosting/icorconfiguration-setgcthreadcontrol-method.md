---
title: ICorConfiguration::SetGCThreadControl, méthode
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
ms.openlocfilehash: 28b012bbe3f8c11ecd0afb8b5905336bd99c349c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724024"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a>ICorConfiguration::SetGCThreadControl, méthode

Définit l’interface de rappel pour les threads de planification pour les tâches non-Runtime qui seraient sinon bloquées pour un garbage collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pGCThreadControl`  
 dans Pointeur vers un objet [IGCThreadControl](igcthreadcontrol-interface.md) qui avertit l’hôte de la suspension des threads pour les tâches qui ne sont pas au moment de l’exécution.  
  
## <a name="remarks"></a>Remarques  

 L’hôte peut choisir dans le rappel [IGCThreadControl :: ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) s’il faut replanifier un thread.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorConfiguration, interface](icorconfiguration-interface.md)
