---
title: IMetaDataImport::EnumInterfaceImpls, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: 910c40413075131765a37e00703ac892e3f39641
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492185"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls, méthode
Énumère toutes les interfaces implémentées par le spécifié `TypeDef` .
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `phEnum`  
 [in, out] Pointeur vers l’énumérateur.  
  
 `td`  
 dans Jeton du TypeDef dont les jetons MethodDef représentant des implémentations d’interface doivent être énumérés.  
  
 `rImpls`  
 à Tableau utilisé pour stocker les jetons MethodDef.  
  
 `cMax`  
 dans Longueur maximale du `rImpls` tableau.  
  
 `pcImpls`  
 à Nombre réel de jetons retournés dans `rImpls` .  
  
## <a name="return-value"></a>Valeur renvoyée  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls`retourné avec succès.|  
|`S_FALSE`|Il n’y a aucun jeton MethodDef à énumérer. Dans ce cas, `pcImpls` a la valeur zéro.|  

## <a name="remarks"></a>Remarques

L’énumération retourne une collection de `mdInterfaceImpl` jetons pour chaque interface implémentée par le spécifié `TypeDef` . Les jetons d’interface sont retournés dans l’ordre dans lequel les interfaces ont été spécifiées (par le biais de `DefineTypeDef` ou `SetTypeDefProps` ). Les propriétés des jetons retournés `mdInterfaceImpl` peuvent être interrogées à l’aide de [GetInterfaceImplProps,](imetadataimport-getinterfaceimplprops-method.md).
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
