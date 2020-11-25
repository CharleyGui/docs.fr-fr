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
ms.openlocfilehash: 1e1a86cdf55812197aae653dca256fb910a7f168
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733891"
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
 [in]. `mdAssembly`Jeton de métadonnées qui représente l’assembly pour lequel obtenir les propriétés.  
  
 `ppbPublicKey`  
 à Pointeur vers la clé publique ou le jeton de métadonnées.  
  
 `pcbPublicKey`  
 à Nombre d’octets dans la clé publique retournée.  
  
 `pulHashAlgId`  
 à Pointeur vers l’algorithme utilisé pour hacher les fichiers dans l’assembly.  
  
 `szName`  
 à Nom simple de l’assembly.  
  
 `cchName`  
 dans Taille, en caractères larges, de `szName` .  
  
 `pchName`  
 à Nombre de caractères larges réellement retournés dans `szName` .  
  
 `pMetaData`  
 à Pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées de l’assembly.  
  
 `pdwAssemblyFlags`  
 à Indicateurs qui décrivent les métadonnées appliquées à un assembly. Cette valeur est une combinaison d’une ou plusieurs valeurs [CorAssemblyFlags,](corassemblyflags-enumeration.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyImport, interface](imetadataassemblyimport-interface.md)
