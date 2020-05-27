---
title: IManagedObject::GetSerializedBuffer, méthode
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
ms.openlocfilehash: c68ec0b41bb38afc7cefaf47df718fffcf42d250
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842427"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a>IManagedObject::GetSerializedBuffer, méthode
Obtient la représentation sous forme de chaîne de cet objet managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pBSTR`  
 à Pointeur vers une chaîne qui est l’objet sérialisé.  
  
## <a name="remarks"></a>Remarques  
 La `GetSerializedBuffer` méthode sérialise l’objet afin qu’il puisse être marshalé vers le client.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IManagedObject, interface](imanagedobject-interface.md)
