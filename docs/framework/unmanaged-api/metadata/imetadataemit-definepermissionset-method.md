---
title: IMetaDataEmit::DefinePermissionSet, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
ms.openlocfilehash: 3698525c139ed52b59ca577c598e675b6c26eef4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719513"
---
# <a name="imetadataemitdefinepermissionset-method"></a>IMetaDataEmit::DefinePermissionSet, méthode

Crée une définition pour un jeu d’autorisations avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition de jeu d’autorisations.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `tk`  
 dans Objet à décoréer.  
  
 `dwAction`  
 dans Valeur [CorDeclSecurity,](cordeclsecurity-enumeration.md) qui spécifie le type de sécurité déclarative à utiliser.  
  
 `pvPermission`  
 dans Objet BLOB d’autorisations.  
  
 `cbPermission`  
 dans Taille, en octets, de `pvPermission` .  
  
 `ppm`  
 à Jeton d’autorisation retourné.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
