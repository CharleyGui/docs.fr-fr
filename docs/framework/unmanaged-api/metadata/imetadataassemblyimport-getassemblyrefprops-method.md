---
title: IMetaDataAssemblyImport::GetAssemblyRefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
ms.openlocfilehash: 2858e924ab6effe192955ce53dad9d333d2d244d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009065"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps, méthode
Obtient le jeu de propriétés pour la référence d’assembly avec la signature de métadonnées spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,
    [out] const void          **ppbPublicKeyOrToken,
    [out] ULONG                *pcbPublicKeyOrToken,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] ASSEMBLYMETADATA     *pMetaData,
    [out] const void           **ppbHashValue,
    [out] ULONG                *pcbHashValue,
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `mdar`  
 dans `mdAssemblyRef`Jeton de métadonnées qui représente la référence d’assembly pour laquelle obtenir les propriétés.  
  
 `ppbPublicKeyOrToken`  
 à Pointeur vers la clé publique ou le jeton de métadonnées.  
  
 `pcbPublicKeyOrToken`  
 à Nombre d’octets dans la clé publique ou le jeton retourné.  
  
 `szName`  
 à Nom simple de l’assembly.  
  
 `cchName`  
 dans Taille, en caractères larges, de `szName` .  
  
 `pchName`  
 à Pointeur vers le nombre de caractères larges réellement retournés dans `szName` .  
  
 `pMetaData`  
 à Pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées de l’assembly.  
  
 `ppbHashValue`  
 à Pointeur vers la valeur de hachage. Il s’agit du hachage, à l’aide de l’algorithme SHA-1, de la `PublicKey` propriété de l’assembly référencé, à moins que l’indicateur arfFullOriginator de l’énumération [AssemblyRefFlags,](assemblyrefflags-enumeration.md) soit défini.  
  
 `pcbHashValue`  
 à Nombre de caractères larges dans la valeur de hachage retournée.  
  
 `pdwAssemblyRefFlags`  
 à Pointeur vers des indicateurs qui décrivent les métadonnées appliquées à un assembly. La valeur flags est une combinaison d’une ou plusieurs valeurs [CorAssemblyFlags,](corassemblyflags-enumeration.md) .  
  
## <a name="return-value"></a>Valeur renvoyée  
 Cette méthode retourne S_OK si elle est réussie ; Sinon, elle retourne l’un des codes d’erreur définis dans le fichier d’en-tête winerror. h.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](imetadataassemblyimport-interface.md)
