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
ms.openlocfilehash: 6d783e27c60db7381025f3b2382728e3996323ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725727"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a>IMetaDataAssemblyEmit::DefineAssembly, méthode

Crée une `Assembly` structure contenant les métadonnées pour l’assembly spécifié et retourne le jeton de métadonnées associé.  
  
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
 dans Clé publique qui identifie le serveur de publication de l’assembly, ou NULL si l’assembly n’a pas un nom fort.  
  
 `cbPublicKey`  
 dans Taille en octets de `pbPublicKey` .  
  
 `uHashAlgId`  
 dans Identificateur de l’algorithme de hachage à utiliser pour chiffrer les fichiers de l’assembly, ou NULL pour spécifier l’algorithme SHA-1.  
  
 `szName`  
 dans Nom de texte explicite de l’assembly. Cette valeur ne doit pas dépasser 1024 caractères.  
  
 `pMetaData`  
 dans Pointeur vers une instance ASSEMBLYMETADATA qui contient les informations relatives à la version, à la plateforme et aux paramètres régionaux de l’assembly.  
  
 `dwAssemblyFlags`  
 dans Combinaison de valeurs [CorAssemblyFlags,](corassemblyflags-enumeration.md) qui décrivent les fonctionnalités de l’assembly.  
  
 `pmda`  
 à Pointeur vers le jeton de métadonnées.  
  
## <a name="remarks"></a>Remarques  

 Une seule `Assembly` structure de métadonnées peut être définie dans un manifeste.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](imetadataassemblyemit-interface.md)
