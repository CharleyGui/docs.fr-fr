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
ms.openlocfilehash: dae4a36537eeac58ffb17ebc1b78d935ec807cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175978"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps, méthode
Obtient les propriétés du fichier avec la signature spécifiée de métadonnées.  
  
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
 [dans] Le `mdFile` jeton de métadonnées qui représente le fichier pour lequel obtenir les propriétés.  
  
 `szName`  
 [out] Le nom simple du fichier.  
  
 `cchName`  
 [dans] La taille, en chars `szName`larges, de .  
  
 `pchName`  
 [out] Le nombre de chars `szName`larges effectivement retourné dans .  
  
 `ppbHashValue`  
 [out] Un pointeur à la valeur de hachage. C’est le hachage, en utilisant l’algorithme SHA-1, du fichier.  
  
 `pcbHashValue`  
 [out] Le nombre de chars larges dans la valeur de hachage retourné.  
  
 `pdwFileFlags`  
 [out] Un pointeur pour les drapeaux qui décrivent les métadonnées appliquées à un fichier. La valeur des drapeaux est une combinaison d’une ou plusieurs valeurs [CorFileFlags.](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
