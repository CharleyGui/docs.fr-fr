---
title: IGCHostControl::RequestVirtualMemLimit, méthode
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
ms.openlocfilehash: d4814e44b1a5311cf6800c804df7a7e11000cbab
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805134"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a>IGCHostControl::RequestVirtualMemLimit, méthode
Demande à l’hôte de modifier les limites de la mémoire virtuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `sztMaxVirtualMemMB`  
 dans Taille de mémoire demandée à allouer.  
  
 `psztNewMaxVirtualMemMB`  
 [in, out] Pointeur vers la taille réelle de la mémoire allouée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IGCHostControl, interface](igchostcontrol-interface.md)
