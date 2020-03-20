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
ms.openlocfilehash: 388f227377ddf73fe1297e1c777bb1c0607c13d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177883"
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
 [dans] Le nom du type à exporter. Pour la version 1.1 de l’heure courante, le nom du type `TypeDef` exporté doit exactement correspondre au nom donné dans le type.  
  
 `tkImplementation`  
 [dans] Un jeton précisant où le type exporté est implémenté. Les valeurs valides et leurs significations associées sont les suivante :  
  
- `mdFile`Le type est implémenté dans un fichier différent au sein de cette assemblée.  
  
- `mdAssemblyRef`Le type est mis en œuvre dans un assemblage différent.  
  
- `mdExportedTYpe`Le type est imbriqué dans un autre type.  
  
- `mdFileNil`Le type est dans le même fichier que le manifeste et n’est pas un type imbriqué.  
  
 `tkTypeDef`  
 [dans] Un jeton aux métadonnées qui spécifie le type à exporter. Cette valeur est `TypeDef` saisie dans le tableau du fichier qui implémente le type et n’est pertinente que si ce fichier est dans cette assemblée.  
  
 `dwExportedTypeFlags`  
 [dans] Une combinaison bitwise de valeurs d’énumération [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) qui définissent les paramètres de propriété pour le type exporté.  
  
 `pmdct`  
 [out] Un pointeur sur les métadonnées retournées qui indique le type exporté.  
  
## <a name="remarks"></a>Notes   
 Une `ExportedType` structure de métadonnées doit être définie pour chaque type exposé par cet assemblage et qui est implémentée dans un module autre que celui contenant le manifeste.  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
