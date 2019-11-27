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
ms.openlocfilehash: c3c57074ae53e2e1d8d41aa04cb6eb6089db58b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449432"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a>IMetaDataAssemblyImport::GetAssemblyProps, méthode
Obtient le jeu de propriétés de l’assembly avec la signature de métadonnées spécifiée.  
  
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
 [in]. `mdAssembly` jeton de métadonnées qui représente l’assembly pour lequel obtenir les propriétés.  
  
 `ppbPublicKey`  
 à Pointeur vers la clé publique ou le jeton de métadonnées.  
  
 `pcbPublicKey`  
 à Nombre d’octets dans la clé publique retournée.  
  
 `pulHashAlgId`  
 à Pointeur vers l’algorithme utilisé pour hacher les fichiers dans l’assembly.  
  
 `szName`  
 à Nom simple de l’assembly.  
  
 `cchName`  
 dans Taille, en caractères larges, de `szName`.  
  
 `pchName`  
 à Nombre de caractères larges réellement retournés dans `szName`.  
  
 `pMetaData`  
 à Pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées de l’assembly.  
  
 `pdwAssemblyFlags`  
 à Indicateurs qui décrivent les métadonnées appliquées à un assembly. Cette valeur est une combinaison d’une ou plusieurs valeurs [CorAssemblyFlags,](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) .  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
