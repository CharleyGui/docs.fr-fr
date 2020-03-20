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
ms.openlocfilehash: 5aa5d78faa8ca9261594e2a649b11088e1d78ee7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177867"
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
 [dans] Un jeton de métadonnées de type `mdtFile` ou `mdtAssemblyRef` qui cartes au fournisseur de ressources. Une valeur NULL indique que le fichier dans lequel les métadonnées sont intégrées est le fournisseur de ressources.  
  
 `dwOffset`  
 [dans] La compensation au début de la ressource dans le fichier. Pour les ressources dans les fichiers autonomes, ce sera toujours zéro. Si la ressource est intégrée dans un fichier PE (portable exécutable), il s’agit d’un décalage de la ressource BLOB, qui commence à l’emplacement spécifié dans le fichier d’en-tête cor.h.  
  
 `dwResourceFlags`  
 [dans] Une combinaison peu sage de valeurs de drapeau qui spécifient les paramètres de propriété pour la définition de ressource.  
  
 `pmdmr`  
 [out] Un pointeur sur le jeton des métadonnées retournées.  
  
## <a name="remarks"></a>Notes   
 Une `ManifestResource` structure de métadonnées doit être définie pour chaque ressource mise en œuvre dans chacun des dossiers de l’assemblée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
