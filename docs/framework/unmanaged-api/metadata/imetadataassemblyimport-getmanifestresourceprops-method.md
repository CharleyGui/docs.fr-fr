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
ms.openlocfilehash: d87d0d46ede65cf44c84edba92fe246174088a4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177664"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a>IMetaDataAssemblyImport::GetManifestResourceProps, méthode
Obtient l’ensemble des propriétés de la ressource manifeste avec la signature spécifiée de métadonnées.  
  
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
 [dans] Un `mdManifestResource` jeton qui représente la ressource pour laquelle obtenir les propriétés.  
  
 `szName`  
 [out] Le nom de la ressource.  
  
 `cchName`  
 [dans] La taille, en chars `szName`larges, de .  
  
 `pchName`  
 [out] Un pointeur sur le nombre de `szName`chars larges effectivement retourné dans .  
  
 `ptkImplementation`  
 [out] Un pointeur `mdFile` à un `mdAssemblyRef` jeton ou un jeton qui représente le fichier ou l’assemblage, respectivement, qui contient la ressource.  
  
 `pdwOffset`  
 [out] Un pointeur à une valeur qui spécifie le décalage au début de la ressource dans le fichier.  
  
 `pdwResourceFlags`  
 [out] Un pointeur pour les drapeaux qui décrivent les métadonnées appliquées à une ressource. La valeur des drapeaux est une combinaison d’une ou plusieurs valeurs [CorManifestResourceFlags.](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md)  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
