---
title: IMetaDataAssemblyImport::GetExportedTypeProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8dd1daf3528bbc642033e254a809c18c3662ff1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779181"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps, méthode
Obtient le jeu de propriétés du type exporté avec la signature de métadonnées spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `mdct`  
 [in] Un `mdExportedType` jeton de métadonnées qui représente le type exporté.  
  
 `szName`  
 [out] Le nom du type exporté.  
  
 `cchName`  
 [in] La taille, en caractères larges, de `szName`.  
  
 `pchName`  
 [out] Le nombre de caractères larges réellement retournés dans `szName`  
  
 `ptkImplementation`  
 [out] Un `mdFile`, `mdAssemblyRef`, ou `mdExportedType` jeton de métadonnées qui contienne ou autorise l’accès aux propriétés du type exporté.  
  
 `ptkTypeDef`  
 [out] Un pointeur vers un `mdTypeDef` jeton qui représente un type dans le fichier.  
  
 `pdwExportedTypeFlags`  
 [out] Pointeur vers les indicateurs qui décrivent les métadonnées appliquées pour le type exporté. La valeur des indicateurs peut être une ou plusieurs [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) valeurs.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
