---
title: IMetaDataEmit::SetPermissionSetProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: 1e6ee1f2f497ef30a5390e7afac55c54705248ed
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007804"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a>IMetaDataEmit::SetPermissionSetProps, méthode
Définit ou met à jour les fonctionnalités de la signature de métadonnées d’un jeu d’autorisations défini par un appel antérieur à [IMetaDataEmit ::D efinepermissionset](imetadataemit-definepermissionset-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `tk`  
 dans Jeton de métadonnées qui représente l’objet à décoréer.  
  
 `dwAction`  
 dans Valeur [CorDeclSecurity,](cordeclsecurity-enumeration.md) qui spécifie le type de sécurité déclarative à utiliser.  
  
 `pvPermission`  
 dans Objet BLOB d’autorisations.  
  
 `cbPermission`  
 dans Taille, en octets, de `pvPermission` .  
  
 `ppm`  
 à Un `mdPermission` jeton de métadonnées qui représente les autorisations mises à jour.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
