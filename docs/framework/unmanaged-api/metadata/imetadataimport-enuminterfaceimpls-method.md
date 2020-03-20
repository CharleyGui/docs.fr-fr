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
ms.openlocfilehash: b535fdd5027a26cc4dd0eafec9883f0186773dd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175497"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls, méthode
Énumère toutes les interfaces mises `TypeDef`en œuvre par les spécifiés .
  
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
 [dans, dehors] Un pointeur à l’enumérateur.  
  
 `td`  
 [dans] Le jeton du TypeDef dont les jetons MethodDef représentant les implémentations d’interface doivent être énumérés.  
  
 `rImpls`  
 [out] Le tableau utilisé pour stocker les jetons MethodDef.  
  
 `cMax`  
 [dans] La longueur maximale `rImpls` du tableau.  
  
 `pcImpls`  
 [out] Le nombre réel de jetons retournés dans `rImpls`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls`retourné avec succès.|  
|`S_FALSE`|Il n’y a pas de jetons MethodDef à énumérer. Dans ce `pcImpls` cas, est réglé à zéro.|  

## <a name="remarks"></a>Notes 

L’énumération renvoie `mdInterfaceImpl` une collection de jetons pour `TypeDef`chaque interface implémentée par le spécifié . Les jetons d’interface sont retournés dans `DefineTypeDef` l’ordre les interfaces ont été spécifiées (par ou). `SetTypeDefProps` Propriétés des `mdInterfaceImpl` jetons retournés peuvent être interrogés à l’aide [de GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
