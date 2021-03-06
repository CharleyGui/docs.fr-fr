---
title: IMetaDataAssemblyImport::GetFileProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: 0b9ff2716cc0bc32c81fe6fcdd4e6c367d4d835f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718174"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps, méthode

Obtient les propriétés du fichier avec la signature de métadonnées spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,
    [out] LPWSTR      szName,
    [in]  ULONG       cchName,
    [out] ULONG       *pchName,
    [out] const void  **ppbHashValue,
    [out] ULONG       *pcbHashValue,
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `mdf`  
 dans `mdFile` Jeton de métadonnées qui représente le fichier pour lequel obtenir les propriétés.  
  
 `szName`  
 à Nom simple du fichier.  
  
 `cchName`  
 dans Taille, en caractères larges, de `szName` .  
  
 `pchName`  
 à Nombre de caractères larges réellement retournés dans `szName` .  
  
 `ppbHashValue`  
 à Pointeur vers la valeur de hachage. Il s’agit du hachage, à l’aide de l’algorithme SHA-1, du fichier.  
  
 `pcbHashValue`  
 à Nombre de caractères larges dans la valeur de hachage retournée.  
  
 `pdwFileFlags`  
 à Pointeur vers les indicateurs qui décrivent les métadonnées appliquées à un fichier. La valeur flags est une combinaison d’une ou plusieurs valeurs [CorFileFlags,](corfileflags-enumeration.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](imetadataassemblyimport-interface.md)
