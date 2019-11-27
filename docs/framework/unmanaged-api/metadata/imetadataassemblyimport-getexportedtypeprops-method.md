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
ms.openlocfilehash: 82302124828a2dab73b445128d7d847e112edd36
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448221"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps, méthode
Obtient le jeu de propriétés du type exporté avec la signature de métadonnées spécifiée.  
  
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
 dans `mdExportedType` jeton de métadonnées qui représente le type exporté.  
  
 `szName`  
 à Nom du type exporté.  
  
 `cchName`  
 dans Taille, en caractères larges, de `szName`.  
  
 `pchName`  
 à Nombre de caractères larges réellement retournés dans `szName`  
  
 `ptkImplementation`  
 à Un `mdFile`, `mdAssemblyRef`ou un jeton de métadonnées de `mdExportedType` qui contient ou autorise l’accès aux propriétés du type exporté.  
  
 `ptkTypeDef`  
 à Pointeur vers un `mdTypeDef` jeton qui représente un type dans le fichier.  
  
 `pdwExportedTypeFlags`  
 à Pointeur vers les indicateurs qui décrivent les métadonnées appliquées au type exporté. La valeur flags peut être une ou plusieurs valeurs [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) .  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
