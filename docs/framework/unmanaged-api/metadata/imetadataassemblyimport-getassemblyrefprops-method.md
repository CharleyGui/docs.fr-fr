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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa633d554652050af51065e11221f898b34d5c63
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772672"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps, méthode
Obtient le jeu de propriétés pour la référence d’assembly avec la signature de métadonnées spécifié.  
  
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
 [in] Le `mdAssemblyRef` jeton de métadonnées qui représente la référence d’assembly pour lequel obtenir les propriétés.  
  
 `ppbPublicKeyOrToken`  
 [out] Pointeur vers la clé publique ou le jeton de métadonnées.  
  
 `pcbPublicKeyOrToken`  
 [out] Le nombre d’octets dans la retourné clé publique ou jeton.  
  
 `szName`  
 [out] Le nom simple de l’assembly.  
  
 `cchName`  
 [in] La taille, en caractères étendus de `szName`.  
  
 `pchName`  
 [out] Un pointeur vers le nombre de caractères étendus réellement retournés dans `szName`.  
  
 `pMetaData`  
 [out] Pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées de l’assembly.  
  
 `ppbHashValue`  
 [out] Pointeur vers la valeur de hachage. Il s’agit du hachage, à l’aide de l’algorithme SHA-1, de la `PublicKey` propriété de l’assembly référencé, à moins que l’arfFullOriginator indicateur de la [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) énumération est définie.  
  
 `pcbHashValue`  
 [out] Le nombre de caractères étendus dans la valeur de hachage retournée.  
  
 `pdwAssemblyRefFlags`  
 [out] Un pointeur vers les indicateurs qui décrivent les métadonnées appliquées à un assembly. La valeur des indicateurs est une combinaison d’une ou plusieurs [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valeurs.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne S_OK en cas de réussite ; Sinon, elle retourne un des codes d’erreur définis dans le fichier d’en-tête Winerror.h.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
