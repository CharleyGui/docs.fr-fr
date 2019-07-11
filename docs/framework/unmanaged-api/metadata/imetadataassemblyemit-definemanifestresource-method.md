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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 781953fe5bf209f195ef4887dff45e1902741f0c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775311"
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
 [in] Le nom de la ressource.  
  
 `tkImplementation`  
 [in] Un jeton de métadonnées de type `mdtFile` ou `mdtAssemblyRef` qui mappe au fournisseur de ressources. Une valeur NULL indique que le fichier dans lequel les métadonnées sont incorporées est le fournisseur de ressources.  
  
 `dwOffset`  
 [in] Offset au début de la ressource dans le fichier. Pour les ressources dans les fichiers autonomes, il sera toujours égal à zéro. Si la ressource est incorporée dans un fichier PE (exécutable portable), il s’agit d’un décalage de l’objet BLOB, qui démarre à l’emplacement spécifié dans le fichier d’en-tête cor.h de ressources.  
  
 `dwResourceFlags`  
 [in] Une combinaison au niveau du bit des valeurs d’indicateurs qui spécifient les paramètres de propriété pour la définition de ressource.  
  
 `pmdmr`  
 [out] Pointeur vers le jeton de métadonnées retournées.  
  
## <a name="remarks"></a>Notes  
 Un seul `ManifestResource` structure des métadonnées doit être définie pour chaque ressource est implémentée dans chacun des fichiers de l’assembly.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateforme :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
