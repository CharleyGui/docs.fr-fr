---
title: IMetaDataAssemblyEmit::SetFileProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetFileProps
helpviewer_keywords:
- IMetaDataAssemblyEmit::SetFileProps method [.NET Framework metadata]
- SetFileProps method [.NET Framework metadata]
ms.assetid: 85667d38-611c-45a9-938d-930ac7a7b681
topic_type:
- apiref
ms.openlocfilehash: 25baa6ffda3d50915cc7898275d6a557c1b3e947
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176030"
---
# <a name="imetadataassemblyemitsetfileprops-method"></a>IMetaDataAssemblyEmit::SetFileProps, méthode
Modifie la structure de métadonnées `File` spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetFileProps (  
    [in] mdFile        file,  
    [in] const void    *pbHashValue,
    [in] ULONG         cbHashValue,  
    [in] DWORD         dwFileFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `file`  
 [dans] Le jeton des métadonnées `File` qui spécifie la structure des métadonnées à modifier.  
  
 `pbHashValue`  
 [dans] Un pointeur vers les données de hachage associées au fichier.  
  
 `cbHashValue`  
 [dans] La taille dans `pbHashValue`les octets de .  
  
 `dwFileFlags`  
 [dans] Une combinaison bitwise de valeurs [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) qui spécifient différents attributs du fichier.  
  
## <a name="remarks"></a>Notes   
 Pour créer `File` une structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit::DefineFile.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
