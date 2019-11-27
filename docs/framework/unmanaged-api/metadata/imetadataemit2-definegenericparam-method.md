---
title: IMetaDataEmit2::DefineGenericParam, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: 3898b095809e2b84f71aba2036f4d7a294dfdf6a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444652"
---
# <a name="imetadataemit2definegenericparam-method"></a>IMetaDataEmit2::DefineGenericParam, méthode
Crée une définition pour un paramètre de type générique et obtient un jeton pour ce paramètre de type générique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineGenericParam (   
    [in]  mdToken         tk,   
    [in]  ULONG           ulParamSeq,   
    [in]  DWORD           dwParamFlags,   
    [in]  LPCWSTR         szname,   
    [in]  DWORD           reserved,   
    [in]  mdToken         rtkConstraints[],   
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `tk`  
 dans Jeton `mdTypeDef` ou `mdMethodDef` qui représente la méthode ou le constructeur pour lequel définir un paramètre générique.  
  
 `ulParamSeq`  
 dans Index du paramètre générique.  
  
 `dwParamFlags`  
 dans Valeur de l’énumération [CorGenericParamAttr,](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) qui décrit le type du paramètre générique.  
  
 `szname`  
 dans Nom du paramètre.  
  
 `reserved`  
 dans Ce paramètre est réservé pour une future extensibilité.  
  
 `rtkConstraints`  
 dans Tableau de contraintes de type se terminant par zéro. Les membres de tableau doivent être un jeton de métadonnées `mdTypeDef`, `mdTypeRef`ou `mdTypeSpec`.  
  
 `pgp`  
 à Jeton qui représente le paramètre générique.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
