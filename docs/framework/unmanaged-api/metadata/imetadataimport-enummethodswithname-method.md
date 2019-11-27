---
title: IMetaDataImport::EnumMethodsWithName, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
ms.openlocfilehash: b0817288040550b5f4c3c4ec063f6a7fdb004137
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450060"
---
# <a name="imetadataimportenummethodswithname-method"></a>IMetaDataImport::EnumMethodsWithName, méthode
Énumère les méthodes portant le nom spécifié et définies par le type référencé par le jeton TypeDef spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `phEnum`  
 [in, out] Pointeur vers l’énumérateur. Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.  
  
 `cl`  
 dans Jeton TypeDef représentant le type dont les méthodes doivent être énumérées.  
  
 `szName`  
 dans Nom qui limite l’étendue de l’énumération.  
  
 `rMethods`  
 à Tableau utilisé pour stocker les jetons MethodDef.  
  
 `cMax`  
 [in] Taille maximale du tableau `rMethods`.  
  
 `pcTokens`  
 à Nombre de jetons MethodDef retournés dans `rMethods`.  
  
## <a name="remarks"></a>Notes  
 Cette méthode énumère les champs et les méthodes, mais pas les propriétés ou les événements. Contrairement à [IMetaDataImport :: EnumMethods,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` ignore tous les jetons de méthode qui n’ont pas le nom spécifié.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodsWithName` retourné avec succès.|  
|`S_FALSE`|Il n’y a aucun jeton à énumérer. Dans ce cas, `pcTokens` est égal à zéro.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
