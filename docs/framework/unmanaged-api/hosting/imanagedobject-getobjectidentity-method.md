---
title: IManagedObject::GetObjectIdentity, méthode
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
ms.openlocfilehash: 1b40ed8e107d30c22b4ade25d29376b1b74583d1
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842411"
---
# <a name="imanagedobjectgetobjectidentity-method"></a>IManagedObject::GetObjectIdentity, méthode
Obtient l’identité de cet objet managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pBSTRGUID`  
 à Pointeur vers le GUID du processus dans lequel l’objet réside.  
  
 `AppDomainID`  
 à Pointeur vers l’ID du domaine d’application de l’objet.  
  
 `pCCW`  
 à Pointeur vers l’index de l’objet dans la table v classique COM.  
  
## <a name="remarks"></a>Remarques  
 L’identité d’un objet géré comprend le GUID du processus, l’ID de domaine d’application et l’index de l’objet dans la table v Classic COM.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IManagedObject, interface](imanagedobject-interface.md)
