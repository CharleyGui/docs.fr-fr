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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b4d143d8dd5391283736d0140e8f1ced1dec53e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775327"
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
 [in] Le nom du type à exporter. Pour la version 1.1 du common language runtime, le nom du type exporté doit correspondre exactement au nom donné dans le `TypeDef` pour le type.  
  
 `tkImplementation`  
 [in] Jeton spécifiant où le type exporté est implémenté. Les valeurs valides et leurs significations associées sont :  
  
- `mdFile` Le type est implémenté dans un fichier différent au sein de cet assembly.  
  
- `mdAssemblyRef` Le type est implémenté dans un autre assembly.  
  
- `mdExportedTYpe` Le type est imbriqué dans un autre type.  
  
- `mdFileNil` Le type est dans le même fichier que le manifeste et n’est pas un type imbriqué.  
  
 `tkTypeDef`  
 [in] Un jeton de métadonnées qui spécifie le type à exporter. Cette valeur est entrée dans le `TypeDef` table dans le fichier qui implémente le type et est pertinente uniquement si ce fichier se trouve dans cet assembly.  
  
 `dwExportedTypeFlags`  
 [in] Une combinaison au niveau du bit de [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) des valeurs d’énumération qui définissent les paramètres de propriété pour le type exporté.  
  
 `pmdct`  
 [out] Pointeur vers le jeton de métadonnées retourné qui indique le type exporté.  
  
## <a name="remarks"></a>Notes  
 Un `ExportedType` structure des métadonnées doit être définie pour chaque type qui est exposé par cet assembly et qui est implémenté dans un module autre que celui qui contient le manifeste.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateforme :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
