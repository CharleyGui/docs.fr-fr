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
ms.openlocfilehash: 1868d13a9dbb73dbdf64e49c395bdbff02ce89d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177455"
---
# <a name="imetadataemit2definegenericparam-method"></a>IMetaDataEmit2::DefineGenericParam, méthode
Crée une définition pour un paramètre de type générique, et obtient un jeton à ce paramètre de type générique.  
  
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
 [dans] Un `mdTypeDef` `mdMethodDef` ou un jeton qui représente la méthode ou le constructeur pour lequel définir un paramètre générique.  
  
 `ulParamSeq`  
 [dans] L’index du paramètre générique.  
  
 `dwParamFlags`  
 [dans] Une valeur de l’énumération [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) qui décrit le type pour le paramètre générique.  
  
 `szname`  
 [dans] Le nom du paramètre.  
  
 `reserved`  
 [dans] Ce paramètre est réservé à l’extéabilité future.  
  
 `rtkConstraints`  
 [dans] Un éventail de contraintes de type à durée nulle. Les membres du `mdTypeDef` `mdTypeRef`tableau `mdTypeSpec` doivent être un jeton, ou métadonnées.  
  
 `pgp`  
 [out] Un jeton qui représente le paramètre générique.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
