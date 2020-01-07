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
ms.openlocfilehash: ef7057ad19fd34750bd15d358e9c1ebb1289cd44
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338062"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a>IMetaDataImport::EnumInterfaceImpls, méthode
Énumère toutes les interfaces implémentées par le `TypeDef`spécifié. 
  
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
  
## <a name="parameters"></a>Parameters  
 `phEnum`  
 [in, out] Pointeur vers l’énumérateur.  
  
 `td`  
 dans Jeton du TypeDef dont les jetons MethodDef représentant des implémentations d’interface doivent être énumérés.  
  
 `rImpls`  
 à Tableau utilisé pour stocker les jetons MethodDef.  
  
 `cMax`  
 dans Longueur maximale du tableau de `rImpls`.  
  
 `pcImpls`  
 à Nombre réel de jetons retournés dans `rImpls`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumInterfaceImpls` retourné avec succès.|  
|`S_FALSE`|Il n’y a aucun jeton MethodDef à énumérer. Dans ce cas, `pcImpls` a la valeur zéro.|  

## <a name="remarks"></a>Notes

L’énumération retourne une collection de `mdInterfaceImpl` jetons pour chaque interface implémentée par le `TypeDef`spécifié. Les jetons d’interface sont retournés dans l’ordre dans lequel les interfaces ont été spécifiées (par `DefineTypeDef` ou `SetTypeDefProps`). Les propriétés des jetons de `mdInterfaceImpl` retournés peuvent être interrogées à l’aide de [GetInterfaceImplProps,](imetadataimport-getinterfaceimplprops-method.md).
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
