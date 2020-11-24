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
ms.openlocfilehash: e28659f3c6912489775dd09951610f19e4400942
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672745"
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
 dans Jeton de métadonnées qui spécifie la `AssemblyRef` structure de métadonnées à modifier.  
  
 `pbPublicKeyOrToken`  
 dans Clé publique de l’éditeur de l’assembly référencé.  
  
 `cbPublicKeyOrToken`  
 dans Taille en octets de `pbPublicKeyOrToken` .  
  
 `szName`  
 dans Nom de texte explicite de l’assembly.  
  
 `pMetaData`  
 dans Pointeur vers une instance ASSEMBLYMETADATA qui contient les informations relatives à la version, à la plateforme et aux paramètres régionaux de l’assembly.  
  
 `pbHashValue`  
 dans Pointeur vers les données de hachage associées à l’assembly.  
  
 `cbHashValue`  
 dans Taille en octets de `pbHashValue` .  
  
 `dwAssemblyRefFlags`  
 dans Combinaison d’opérations de bits de valeurs [AssemblyRefFlags,](assemblyrefflags-enumeration.md) qui spécifient des attributs de l’assembly référencé.  
  
## <a name="remarks"></a>Remarques  

 Pour créer une `AssemblyRef` structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit ::D efineassemblyref](imetadataassemblyemit-defineassemblyref-method.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](imetadataassemblyemit-interface.md)
