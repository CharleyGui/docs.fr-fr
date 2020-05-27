---
title: IMetaDataAssemblyEmit::DefineManifestResource, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 026f5efe195cdb34999b65c5f47de6f68d30e11a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008129"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a>IMetaDataAssemblyEmit::DefineManifestResource, méthode
Crée une structure `ManifestResource` contenant les métadonnées pour la ressource de manifeste spécifiée et retourne le jeton de métadonnées associé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szName`  
 [in] Nom de la ressource.  
  
 `tkImplementation`  
 dans Un jeton de métadonnées de type `mdtFile` ou `mdtAssemblyRef` qui est mappé au fournisseur de ressources. Une valeur NULL indique que le fichier dans lequel les métadonnées sont incorporées est le fournisseur de ressources.  
  
 `dwOffset`  
 dans Offset au début de la ressource dans le fichier. Pour les ressources de fichiers autonomes, cette valeur est toujours égale à zéro. Si la ressource est incorporée dans un fichier PE (exécutable portable), il s’agit d’un décalage de l’objet BLOB de ressources, qui démarre à l’emplacement spécifié dans le fichier d’en-tête Cor. h.  
  
 `dwResourceFlags`  
 dans Combinaison d’opérations de bits de valeurs d’indicateur qui spécifient des paramètres de propriété pour la définition de ressource.  
  
 `pmdmr`  
 à Pointeur vers le jeton de métadonnées retourné.  
  
## <a name="remarks"></a>Remarques  
 Une `ManifestResource` structure de métadonnées doit être définie pour chaque ressource implémentée dans chacun des fichiers de l’assembly.  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](imetadataassemblyemit-interface.md)
