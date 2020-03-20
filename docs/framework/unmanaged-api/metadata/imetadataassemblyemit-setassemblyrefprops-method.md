---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: 6ad6bbb8a4c69f575bbeba3a297c46e049a97325
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176043"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyRefProps, méthode
Modifie la structure de métadonnées `AssemblyRef` spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,
    [in] const ASSEMBLYMETADATA     *pMetaData,
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ar`  
 [dans] Le jeton des métadonnées `AssemblyRef` qui spécifie la structure des métadonnées à modifier.  
  
 `pbPublicKeyOrToken`  
 [dans] La clé publique de l’éditeur de l’assemblée référencée.  
  
 `cbPublicKeyOrToken`  
 [dans] La taille dans `pbPublicKeyOrToken`les octets de .  
  
 `szName`  
 [dans] Le nom de texte lisible par l’homme de l’assemblée.  
  
 `pMetaData`  
 [dans] Un pointeur à une instance ASSEMBLYMETADATA qui contient la version, la plate-forme et les informations locales pour l’assemblage.  
  
 `pbHashValue`  
 [dans] Un pointeur vers les données de hachage associées à l’assemblage.  
  
 `cbHashValue`  
 [dans] La taille dans `pbHashValue`les octets de .  
  
 `dwAssemblyRefFlags`  
 [dans] Une combinaison peu sage des valeurs [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) qui spécifient les attributs de l’assemblage référencé.  
  
## <a name="remarks"></a>Notes   
 Pour créer `AssemblyRef` une structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit::DefineAssemblyRef.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
