---
title: AddFile, méthode
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
ms.openlocfilehash: 53ca4005f5681cfc5d550301d8aad1406aceb3a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717199"
---
# <a name="addfile-method"></a>AddFile, méthode

Ajoute des fichiers à l’assembly. Peut également être utilisé pour créer des modules indépendants.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  

 `AssemblyID`  
 ID unique de l’assembly à augmenter.  
  
 `pszFilename`  
 Nom complet du fichier à ajouter.  
  
 `dwFlags`  
 Indicateurs FileDef COM+ tels que `ffContainsNoMetaData` et `ffWriteable` . `dwFlags` est passé à la [méthode DefineFile](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 Interface d' [interface d’IMetaDataEmit](../metadata/imetadataemit-interface.md) à utiliser pour émettre des métadonnées, si nécessaire.  
  
 `pFileToken`  
 Pointeur vers l’emplacement où l’ID unique du fichier ajouté sera stocké.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 Requiert ALink. h.  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
