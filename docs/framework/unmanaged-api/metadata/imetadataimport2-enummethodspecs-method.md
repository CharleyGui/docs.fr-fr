---
title: IMetaDataImport2::EnumMethodSpecs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 8f6fbc570e7ea85aca5b365611d58a1700fb27cd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490716"
---
# <a name="imetadataimport2enummethodspecs-method"></a>IMetaDataImport2::EnumMethodSpecs, méthode
Obtient un énumérateur pour un tableau de jetons MethodSpec associés au jeton MethodDef ou MemberRef spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a>Paramètres  
 `phEnum`  
 [in, out] Pointeur vers l’énumérateur pour `rMethodSpecs` .  
  
 `tk`  
 dans Jeton MemberRef ou MethodDef qui représente la méthode dont les jetons MethodSpec doivent être énumérés. Si la valeur de `tk` est égale à 0 (zéro), tous les jetons MethodSpec dans l’étendue sont énumérés.  
  
 `rMethodSpecs`  
 à Tableau de jetons MethodSpec à énumérer.  
  
 `cMax`  
 dans Nombre maximal de jetons demandés à placer dans `rMethodSpecs` .  
  
 `pcMethodSpecs`  
 à Nombre retourné de jetons placés dans `rMethodSpecs` .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs`retourné avec succès.|  
|`S_FALSE`|`phEnum`n’a aucun élément membre. Dans ce cas, `pcMethodSpecs` a la valeur 0 (zéro).|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport2, interface](imetadataimport2-interface.md)
- [IMetaDataImport, interface](imetadataimport-interface.md)
