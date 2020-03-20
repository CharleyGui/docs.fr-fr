---
title: IMetaDataEmit::DefineImportType, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177678"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType, méthode
Crée une référence au type spécifié qui est défini en dehors de la portée actuelle, et définit un jeton pour cette référence.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineImportType (
    [in]  IMetaDataAssemblyImport  *pAssemImport,
    [in]  const void               *pbHashValue,
    [in]  ULONG                    cbHashValue,
    [in]  IMetaDataImport          *pImport,
    [in]  mdTypeDef                tdImport,
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pAssemImport`  
 [dans] Une interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) qui représente l’assemblage à partir duquel le type cible est importé.  
  
 `pbHashValue`  
 [dans] Un tableau qui contient le hachage pour l’assemblage spécifié par `pAssemImport`.  
  
 `cbHashValue`  
 [in] Nombre d'octets dans le tableau `pbHashValue`.  
  
 `pImport`  
 [dans] Une interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) qui représente la portée des métadonnées à partir de laquelle le type cible est importé.  
  
 `tdImport`  
 [dans] Un `mdTypeDef` jeton qui spécifie le type de cible.  
  
 `pAssemEmit`  
 [dans] Une interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) qui représente l’assemblage dans lequel le type cible est importé.  
  
 `ptr`  
 [out] Le `mdTypeRef` jeton qui est défini dans la portée actuelle pour la référence de type.  
  
## <a name="remarks"></a>Notes   
 Avant d’appeler la méthode [IMetaDataEmit::DefineImportMember,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) vous `DefineImportType` pouvez utiliser la méthode pour créer une référence type, dans la portée actuelle, pour la classe mère du membre ou l’interface parente.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
