---
title: IHostFilter::MarkToken, méthode
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
ms.openlocfilehash: 11529ce896f265f2b200fa6e511d4b913e9147c8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008220"
---
# <a name="ihostfiltermarktoken-method"></a>IHostFilter::MarkToken, méthode
Indique que le jeton de métadonnées spécifié sera traité.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `tk`  
 dans Jeton de métadonnées à traiter.  
  
## <a name="remarks"></a>Remarques  
 En général, vous souhaitez qu’un jeton soit traité s’il se trouve dans la portée des métadonnées. La `MarkToken` méthode est passée au moteur de métadonnées via la méthode [IMetaDataEmit :: SetHandler](imetadataemit-sethandler-method.md) .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de métadonnées](metadata-interfaces.md)
- [IHostFilter, interface](ihostfilter-interface.md)
