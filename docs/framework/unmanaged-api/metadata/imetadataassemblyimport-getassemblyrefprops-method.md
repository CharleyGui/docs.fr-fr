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
ms.openlocfilehash: 4149db74adfa26df221eed5c590766a023bb105e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448227"
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
 dans `mdAssemblyRef` jeton de métadonnées qui représente la référence d’assembly pour laquelle obtenir les propriétés.  
  
 `ppbPublicKeyOrToken`  
 à Pointeur vers la clé publique ou le jeton de métadonnées.  
  
 `pcbPublicKeyOrToken`  
 à Nombre d’octets dans la clé publique ou le jeton retourné.  
  
 `szName`  
 à Nom simple de l’assembly.  
  
 `cchName`  
 dans Taille, en caractères larges, de `szName`.  
  
 `pchName`  
 à Pointeur vers le nombre de caractères larges réellement retournés dans `szName`.  
  
 `pMetaData`  
 à Pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées de l’assembly.  
  
 `ppbHashValue`  
 à Pointeur vers la valeur de hachage. Il s’agit du hachage, à l’aide de l’algorithme SHA-1, de la propriété `PublicKey` de l’assembly référencé, sauf si l’indicateur arfFullOriginator de l’énumération [AssemblyRefFlags,](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) est défini.  
  
 `pcbHashValue`  
 à Nombre de caractères larges dans la valeur de hachage retournée.  
  
 `pdwAssemblyRefFlags`  
 à Pointeur vers des indicateurs qui décrivent les métadonnées appliquées à un assembly. La valeur flags est une combinaison d’une ou plusieurs valeurs [CorAssemblyFlags,](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) .  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne S_OK si elle est réussie ; Sinon, elle retourne l’un des codes d’erreur définis dans le fichier d’en-tête winerror. h.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
