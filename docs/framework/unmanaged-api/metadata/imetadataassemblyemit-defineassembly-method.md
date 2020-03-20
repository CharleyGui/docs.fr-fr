---
title: IMetaDataAssemblyEmit::DefineAssembly, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 14bd352099890e4ca36321d550b8e982d4373231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177890"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly, méthode
Crée `Assembly` une structure contenant des métadonnées pour l’assemblage spécifié et renvoie le jeton des métadonnées associées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pbPublicKey`  
 [dans] La clé publique qui identifie l’éditeur de l’assemblée, ou NULL si l’assemblée n’est pas fortement nommée.  
  
 `cbPublicKey`  
 [dans] La taille dans `pbPublicKey`les octets de .  
  
 `uHashAlgId`  
 [dans] L’identifiant de l’algorithme de hachage à utiliser pour chiffrer les fichiers dans l’assemblage, ou NULL pour spécifier l’algorithme SHA-1.  
  
 `szName`  
 [dans] Le nom de texte lisible par l’homme de l’assemblée. Cette valeur ne doit pas dépasser 1024 caractères.  
  
 `pMetaData`  
 [dans] Un pointeur à une instance ASSEMBLYMETADATA qui contient la version, la plate-forme et les informations locales pour l’assemblage.  
  
 `dwAssemblyFlags`  
 [dans] Une combinaison de valeurs [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) qui décrivent les caractéristiques de l’assemblage.  
  
 `pmda`  
 [out] Un pointeur vers le jeton des métadonnées.  
  
## <a name="remarks"></a>Notes   
 Une `Assembly` seule structure de métadonnées peut être définie dans un manifeste.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
