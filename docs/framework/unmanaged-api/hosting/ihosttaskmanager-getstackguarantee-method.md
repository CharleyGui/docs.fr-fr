---
title: IHostTaskManager::GetStackGuarantee, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetStackGuarantee
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type:
- apiref
ms.openlocfilehash: d76242eb8539f2e8dffbf39b7eaf595664bdce8e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842021"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a>IHostTaskManager::GetStackGuarantee, méthode
Obtient la quantité d’espace de pile dont la disponibilité est garantie après la fin d’une opération de pile, mais avant la fermeture d’un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pGuarantee`  
 à Pointeur vers le nombre d’octets disponibles.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IHostTaskManager, interface](ihosttaskmanager-interface.md)
