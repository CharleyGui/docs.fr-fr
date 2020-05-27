---
title: IMetaDataAssemblyImport::GetManifestResourceProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: c0b6d53ce3be3aed6a577bf6e38a281928499848
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009026"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps, méthode
Obtient le jeu de propriétés de la ressource de manifeste avec la signature de métadonnées spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `mdmr`  
 dans `mdManifestResource`Jeton qui représente la ressource pour laquelle obtenir les propriétés.  
  
 `szName`  
 à Nom de la ressource.  
  
 `cchName`  
 dans Taille, en caractères larges, de `szName` .  
  
 `pchName`  
 à Pointeur vers le nombre de caractères larges réellement retournés dans `szName` .  
  
 `ptkImplementation`  
 à Pointeur vers un `mdFile` jeton ou un `mdAssemblyRef` jeton qui représente le fichier ou l’assembly, respectivement, qui contient la ressource.  
  
 `pdwOffset`  
 à Pointeur vers une valeur qui spécifie le décalage au début de la ressource dans le fichier.  
  
 `pdwResourceFlags`  
 à Pointeur vers des indicateurs qui décrivent les métadonnées appliquées à une ressource. La valeur flags est une combinaison d’une ou plusieurs valeurs [CorManifestResourceFlags,](cormanifestresourceflags-enumeration.md) .  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](imetadataassemblyimport-interface.md)
