---
title: IMetaDataAssemblyEmit::DefineFile, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: 0b7ca6f9878ed2fa2d90ea93e5101f0a66ec2d5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440207"
---
# <a name="imetadataassemblyemitdefinefile-method"></a>IMetaDataAssemblyEmit::DefineFile, méthode
Crée une structure `File` contenant les métadonnées pour l'assembly référencé par cet assembly et retourne le jeton de métadonnées associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szName`  
 dans Nom du fichier à consommer.  
  
 `pbHashValue`  
 dans Pointeur vers les données de hachage associées à l’assembly.  
  
 `cbHashValue`  
 dans Taille en octets de `pbHashValue`.  
  
 `dwFileFlags`  
 dans Combinaison d’opérations de bits de `FileFlags` valeurs qui spécifient des paramètres de propriété.  
  
 `pmdf`  
 à Pointeur vers le jeton de `File` retourné.  
  
## <a name="remarks"></a>Notes  
 Une `File` structure de métadonnées doit être définie pour chaque fichier qui faisait partie de cet assembly au moment de la génération de cet assembly, à l’exception du fichier qui contient les métadonnées.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
