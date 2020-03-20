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
ms.openlocfilehash: 9aef471c1155070af0e9bcca14975a65bc5dc763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175965"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a>IMetaDataAssemblyImport::GetAssemblyRefProps, méthode
Obtient l’ensemble des propriétés pour la référence d’assemblage avec la signature spécifiée de métadonnées.  
  
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
 [dans] Le `mdAssemblyRef` jeton de métadonnées qui représente la référence d’assemblage pour laquelle obtenir les propriétés.  
  
 `ppbPublicKeyOrToken`  
 [out] Un pointeur à la clé publique ou le jeton des métadonnées.  
  
 `pcbPublicKeyOrToken`  
 [out] Le nombre d’octets dans la clé ou le jeton public retourné.  
  
 `szName`  
 [out] Le nom simple de l’assemblée.  
  
 `cchName`  
 [dans] La taille, en chars `szName`larges, de .  
  
 `pchName`  
 [out] Un pointeur sur le nombre de `szName`chars larges effectivement retourné dans .  
  
 `pMetaData`  
 [out] Un pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées d’assemblage.  
  
 `ppbHashValue`  
 [out] Un pointeur à la valeur de hachage. C’est le hachage, en utilisant l’algorithme SHA-1, de la `PublicKey` propriété de l’assemblage en cours de référence, à moins que le drapeau arfFullOriginator de l’en énumération [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) est fixé.  
  
 `pcbHashValue`  
 [out] Le nombre de chars larges dans la valeur de hachage retourné.  
  
 `pdwAssemblyRefFlags`  
 [out] Un pointeur pour les drapeaux qui décrivent les métadonnées appliquées à un assemblage. La valeur des drapeaux est une combinaison d’une ou plusieurs valeurs [CorAssemblyFlags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode renvoie S_OK si elle réussit; autrement, il renvoie l’un des codes d’erreur définis dans le fichier d’en-tête Winerror.h.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
