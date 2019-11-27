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
ms.openlocfilehash: 44f97ef498eb8e64c55fc86b9f290b9e088293f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432068"
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
  
- `mdFile` le type est implémenté dans un fichier différent au sein de cet assembly.  
  
- `mdAssemblyRef` le type est implémenté dans un assembly différent.  
  
- `mdExportedTYpe` le type est imbriqué dans un autre type.  
  
- `mdFileNil` le type se trouve dans le même fichier que le manifeste et n’est pas un type imbriqué.  
  
 `tkTypeDef`  
 dans Jeton pour les métadonnées qui spécifie le type à exporter. Cette valeur est entrée dans la table `TypeDef` du fichier qui implémente le type et s’applique uniquement si ce fichier se trouve dans cet assembly.  
  
 `dwExportedTypeFlags`  
 dans Combinaison d’opérations de bits de valeurs d’énumération [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) qui définissent les paramètres de propriété pour le type exporté.  
  
 `pmdct`  
 à Pointeur vers le jeton de métadonnées retourné qui indique le type exporté.  
  
## <a name="remarks"></a>Notes  
 Une structure de métadonnées `ExportedType` doit être définie pour chaque type exposé par cet assembly et implémenté dans un module autre que celui contenant le manifeste.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
