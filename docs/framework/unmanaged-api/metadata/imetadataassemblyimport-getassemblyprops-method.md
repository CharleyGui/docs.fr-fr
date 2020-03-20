---
title: IMetaDataAssemblyImport::GetAssemblyProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
ms.openlocfilehash: dfa900e2184a8c415d75f5702c572b14c4018749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177789"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>IMetaDataAssemblyImport::GetAssemblyProps, méthode
Obtient l’ensemble des propriétés pour l’assemblage avec la signature spécifiée de métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `mda`  
 [in]. Le `mdAssembly` jeton de métadonnées qui représente l’assemblage pour lequel obtenir les propriétés.  
  
 `ppbPublicKey`  
 [out] Un pointeur à la clé publique ou le jeton des métadonnées.  
  
 `pcbPublicKey`  
 [out] Le nombre d’octets dans la clé publique retournée.  
  
 `pulHashAlgId`  
 [out] Un pointeur à l’algorithme utilisé pour hachage les fichiers dans l’assemblage.  
  
 `szName`  
 [out] Le nom simple de l’assemblée.  
  
 `cchName`  
 [dans] La taille, en chars `szName`larges, de .  
  
 `pchName`  
 [out] Le nombre de chars `szName`larges effectivement retourné dans .  
  
 `pMetaData`  
 [out] Un pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées d’assemblage.  
  
 `pdwAssemblyFlags`  
 [out] Drapeaux qui décrivent les métadonnées appliquées à un assemblage. Cette valeur est une combinaison d’une ou plusieurs valeurs [CorAssemblyFlags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
