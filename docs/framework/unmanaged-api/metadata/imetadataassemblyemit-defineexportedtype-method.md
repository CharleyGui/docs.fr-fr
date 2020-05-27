---
title: IMetaDataAssemblyEmit::DefineExportedType, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 81d6c972b53221ee53cbcf31639d65c30858b48b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008155"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType, méthode
Crée une structure `ExportedType` contenant les métadonnées pour le type exporté spécifié et retourne le jeton de métadonnées associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szName`  
 dans Nom du type à exporter. Pour la version 1,1 de la common language runtime, le nom du type exporté doit correspondre exactement au nom donné dans le `TypeDef` pour le type.  
  
 `tkImplementation`  
 dans Jeton spécifiant où le type exporté est implémenté. Les valeurs valides et les significations qui leur sont associées sont les suivantes :  
  
- `mdFile`Le type est implémenté dans un fichier différent au sein de cet assembly.  
  
- `mdAssemblyRef`Le type est implémenté dans un assembly différent.  
  
- `mdExportedTYpe`Le type est imbriqué dans un autre type.  
  
- `mdFileNil`Le type se trouve dans le même fichier que le manifeste et n’est pas un type imbriqué.  
  
 `tkTypeDef`  
 dans Jeton pour les métadonnées qui spécifie le type à exporter. Cette valeur est entrée dans la `TypeDef` table du fichier qui implémente le type et s’applique uniquement si ce fichier se trouve dans cet assembly.  
  
 `dwExportedTypeFlags`  
 dans Combinaison d’opérations de bits de valeurs d’énumération [CorTypeAttr](cortypeattr-enumeration.md) qui définissent les paramètres de propriété pour le type exporté.  
  
 `pmdct`  
 à Pointeur vers le jeton de métadonnées retourné qui indique le type exporté.  
  
## <a name="remarks"></a>Remarques  
 Une `ExportedType` structure de métadonnées doit être définie pour chaque type exposé par cet assembly et implémenté dans un module autre que celui contenant le manifeste.  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](imetadataassemblyemit-interface.md)
