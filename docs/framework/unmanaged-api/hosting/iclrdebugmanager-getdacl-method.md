---
title: ICLRDebugManager::GetDacl, méthode
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.GetDacl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::GetDacl
helpviewer_keywords:
- GetDacl method [.NET Framework hosting]
- ICLRDebugManager::GetDacl method [.NET Framework hosting]
ms.assetid: 7115e920-aaff-440a-824e-39497139c6f6
topic_type:
- apiref
ms.openlocfilehash: 8a7de5a900bc1af219924b6a83f83cf7e2ef6150
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726143"
---
# <a name="iclrdebugmanagergetdacl-method"></a>ICLRDebugManager::GetDacl, méthode

Cette méthode n’est pas implémentée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDacl (  
    [out] PACL* ppacl  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ppacl`  
 à Pointeur d’interface vers la liste d’Access Control (ACL).  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|E_NOTIMPL|Cette méthode n'est pas implémentée.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRControl, interface](iclrcontrol-interface.md)
- [ICLRDebugManager, interface](iclrdebugmanager-interface.md)
- [SetDacl, méthode](iclrdebugmanager-setdacl-method.md)
- [IHostControl, interface](ihostcontrol-interface.md)
