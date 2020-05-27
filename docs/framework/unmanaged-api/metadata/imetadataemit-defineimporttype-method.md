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
ms.openlocfilehash: edce5cb93b770fb5730e5a06633ffffacf332f7a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004688"
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
 dans Interface [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) qui représente l’assembly à partir duquel le type cible est importé.  
  
 `pbHashValue`  
 dans Tableau qui contient le hachage de l’assembly spécifié par `pAssemImport` .  
  
 `cbHashValue`  
 [in] Nombre d'octets dans le tableau `pbHashValue`.  
  
 `pImport`  
 dans Interface [IMetaDataImport](imetadataimport-interface.md) qui représente la portée des métadonnées à partir de laquelle le type cible est importé.  
  
 `tdImport`  
 dans `mdTypeDef`Jeton qui spécifie le type de cible.  
  
 `pAssemEmit`  
 dans Interface [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) qui représente l’assembly dans lequel le type cible est importé.  
  
 `ptr`  
 à `mdTypeRef`Jeton qui est défini dans la portée actuelle pour la référence de type.  
  
## <a name="remarks"></a>Remarques  
 Avant d’appeler la méthode [IMetaDataEmit ::D efineimportmember](imetadataemit-defineimportmember-method.md) , vous pouvez utiliser la `DefineImportType` méthode pour créer une référence de type, dans la portée actuelle, pour la classe parente ou l’interface parente du membre.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
