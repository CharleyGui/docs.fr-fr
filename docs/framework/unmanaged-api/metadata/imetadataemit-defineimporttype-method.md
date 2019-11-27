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
ms.openlocfilehash: 5b4b0682b2bddff96cb3d720900ed3aa39f06f9d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431852"
---
# <a name="imetadataemitdefineimporttype-method"></a>IMetaDataEmit::DefineImportType, méthode
Crée une référence au type spécifié qui est défini en dehors de la portée actuelle et définit un jeton pour cette référence.  
  
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
 dans Interface [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) qui représente l’assembly à partir duquel le type cible est importé.  
  
 `pbHashValue`  
 dans Tableau qui contient le hachage de l’assembly spécifié par `pAssemImport`.  
  
 `cbHashValue`  
 [in] Nombre d'octets dans le tableau `pbHashValue`.  
  
 `pImport`  
 dans Interface [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) qui représente la portée des métadonnées à partir de laquelle le type cible est importé.  
  
 `tdImport`  
 dans Jeton `mdTypeDef` qui spécifie le type de cible.  
  
 `pAssemEmit`  
 dans Interface [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) qui représente l’assembly dans lequel le type cible est importé.  
  
 `ptr`  
 à Jeton `mdTypeRef` qui est défini dans la portée actuelle pour la référence de type.  
  
## <a name="remarks"></a>Notes  
 Avant d’appeler la méthode [IMetaDataEmit ::D efineimportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) , vous pouvez utiliser la méthode `DefineImportType` pour créer une référence de type, dans la portée actuelle, pour la classe parente ou l’interface parente du membre.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
