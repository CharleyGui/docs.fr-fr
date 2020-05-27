---
title: IGCHost::SetGCStartupLimits, méthode
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
ms.openlocfilehash: 3b0c11ac9d827bd252018172e2337df653054a7b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805200"
---
# <a name="igchostsetgcstartuplimits-method"></a>IGCHost::SetGCStartupLimits, méthode
Définit la taille du segment et la taille maximale de la génération 0.  
  
> [!IMPORTANT]
> À partir de la .NET Framework 4,5, vous pouvez définir la taille du segment et la taille maximale de la génération 0 sur des valeurs supérieures à à `DWORD` l’aide de la méthode [IGCHost2 :: setgcstartuplimitsex,](igchost2-setgcstartuplimitsex-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `SegmentSize`  
 dans Taille du segment utilisé par le système de garbage collection.  
  
 `MaxGen0Size`  
 dans Taille maximale de la génération 0.  
  
## <a name="remarks"></a>Notes  
 La `SetGCStartupLimits` méthode ne peut être appelée qu’une seule fois. Ces valeurs ne peuvent pas être modifiées ultérieurement.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** GCHost. idl, GCHost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IGCHost, interface](igchost-interface.md)
