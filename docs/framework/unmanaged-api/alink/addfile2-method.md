---
title: AddFile2, méthode
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
ms.openlocfilehash: 8dadf9ec8f896b03e4918b21f5153c1b747010fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446668"
---
# <a name="addfile2-method"></a>AddFile2, méthode
Ajoute des fichiers à l’assembly. Peut également être utilisé pour créer des modules indépendants.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID de l’assembly auquel le fichier est ajouté.  
  
 `pszFilename`  
 Nom du fichier à ajouter.  
  
 `dwFlags`  
 COM+ `FileDef` des indicateurs tels que `ffContainsNoMetaData` et `ffWriteable`. `dwFlags` est passé à la [méthode DefineFile](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 Interface de l’interface de l' [interface IMetaDataEmit2](../metadata/imetadataemit2-interface.md) .  
  
 `pFileToken`  
 Reçoit l’ID du fichier en cours d’ajout.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert ALink. h.  
  
## <a name="see-also"></a>Voir aussi

- [IALink2, interface](ialink2-interface.md)
- [IALink, interface](ialink-interface.md)
- [API ALink](index.md)
